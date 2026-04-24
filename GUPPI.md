# GUPPI / nanoclaw — Development

## What this is
Personalized fork of nanoclaw running GUPPI, a personal AI assistant on a Raspberry Pi 5.
This repo IS the installation — fork it, modify it, make it yours.
Primary interface: Telegram.

## Repos
- **GitHub**: `https://github.com/richardtessier/nanoclaw`
- **Mac (dev)**: `~/cl-ai/pi-nanoclaw/`
- **Pi (prod)**: `~/nanoclaw/` on `ssh.familletessier.com`

## Deployment
```bash
# From Mac: push changes
git push origin main

# On Pi: pull and apply
ssh pi "cd ~/nanoclaw && git pull"
```
SSH alias: `pi` → `ssh.familletessier.com`

## Key files
| File | Purpose |
|------|---------|
| `groups/telegram_main/CLAUDE.md` | GUPPI's per-session instructions — read fresh each container session, no restart needed |
| `groups/telegram_main/HEARTBEAT.md` | Scheduled/proactive tasks |
| `src/` | nanoclaw host process (Node.js) — modify freely via Claude Code |
| `.env` | Credentials — Pi only, never commit |

## Current capabilities
- Telegram messaging
- Web search and fetch
- Scheduled tasks via HEARTBEAT.md

## In-progress
- **Email/mailbox** — provider TBD
- **Google Calendar** — OAuth flow TBD

## Conventions
- Credentials go in `.env` on the Pi only — never commit
- `groups/telegram_main/CLAUDE.md` changes take effect next container session
- `src/` changes require restarting the nanoclaw host process on the Pi
- GUPPI confirms before acting: "⚙️ Starting: [description]" before any multi-step task
