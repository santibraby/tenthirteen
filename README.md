# 10:13

A single-file habit tracking app.

Data is stored in a private companion repo: `tenthirteen-data`, accessed via a fine-grained GitHub Personal Access Token. No Google OAuth, no third-party services.

## Architecture

- `index.html` — the entire app
- Data lives in `tenthirteen-data/data.json` (private repo)
- On first load the app prompts for a GitHub PAT and stores it in `localStorage`

### Question IDs are stable

Questions have stable IDs (m1, m3, d1, h1, etc.). Adding or removing a question never destroys historical data — old entries keep their old keys, new entries include new keys, and the app reads each entry by key so missing fields just display as blank. Never reuse a retired ID.

## PAT setup

Generate a fine-grained PAT at https://github.com/settings/personal-access-tokens/new

- Resource owner: your account
- Repository access: only `tenthirteen-data`
- Permissions:
  - Contents: **Read and write**
  - Metadata: Read (required)

Paste it into the app when prompted.
