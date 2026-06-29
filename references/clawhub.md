# Urufu on ClawHub / OpenClaw

OpenClaw loads **skills** from [ClawHub](https://clawhub.ai). The urufu skill tells your agent how to read portfolio, claim yield, and mint — you bring wallet + RPC.

## Repo

**https://github.com/urufu-labs/urufu-agent**

Clone the repo root — the skill is the whole repository:

```bash
git clone https://github.com/urufu-labs/urufu-agent.git
cd urufu-agent
openclaw skills install ./ --as urufu-agent-play
```

Start a **new OpenClaw session** after install.

On first talk, agent should follow `references/onboarding.md` — ask for RPC, explain Alchemy Base setup, key in `~/.urufu-agent/env`, speak in urufu voice.

Optional steward CLI (recommended for claim timers + EIP-712 signing):

```bash
cd scripts && npm install
```

## What you configure (not urufu)

| Variable | Required | Notes |
|---|---|---|
| `URUFU_WALLET` | yes | Address your agent acts for |
| `URUFU_PRIVATE_KEY` | for writes | Session key on your VM — never main seed in chat |
| `URUFU_RPC_URL` | yes | **Your** Alchemy / QuickNode / Infura Base endpoint |

Public urufu indexer (reads, no key): `https://neochibi-api.radbro.xyz`

## What to say

| Prompt | Action |
|---|---|
| check my urufu | Portfolio + yield + mint phase status |
| claim now | Gasless claim (6h cooldown) |
| mint now | Gasless free allowlist mint |
| mint paid | You pay ETH/URU + gas |

Default: **monitor only** until you give a write command.

## Publish to ClawHub (maintainers)

When ready, publish the skill folder (not the whole monorepo) via `clawhub publish`.

## Related

- Full guide: `docs/agent-play.md`
- Bootstrap prompt: `references/BOOTSTRAP.md`
- Bankr path: `references/bankr.md`
