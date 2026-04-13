# thenemal-cc-marketplace

Personal [Claude Code](https://docs.anthropic.com/en/docs/claude-code) plugin marketplace (`seb-plugins`).

## Plugins

| Plugin | Source repo | Skills |
|--------|------------|--------|
| **tax-tools** | [tax-assistant](https://github.com/thenemal/tax-assistant) | `/tax-review`, `/tax-analysis`, `/tax-anomalies` |
| **bot-ops** | [botnificent-manager](https://github.com/thenemal/botnificent-manager) | `/bot-status`, `/bot-logs`, `/bot-restart`, `/bot-deploy` |

## How it works

This repo contains a single file: `.claude-plugin/marketplace.json`. It acts as a registry — each plugin entry points to a source repo via git URL + pinned SHA. The actual plugin code (skills, commands, agents) lives in those source repos under their own `.claude-plugin/` directories.

Claude Code fetches and caches plugins from the source repos at the pinned commit. Update the SHA in `marketplace.json` when plugin code changes in a source repo.

## Installation

Add this marketplace to Claude Code's `settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "seb-plugins": {
      "source": {
        "source": "git",
        "url": "https://github.com/thenemal/thenemal-cc-marketplace.git"
      },
      "autoUpdate": true
    }
  }
}
```

Then enable individual plugins:

```json
{
  "enabledPlugins": {
    "tax-tools@seb-plugins": true,
    "bot-ops@seb-plugins": true
  }
}
```
