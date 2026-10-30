# DOOM POP TV agent skill

**AI agent is busy coding? Let DOOM POP TV entertain the human.**

[DOOM POP TV](https://tv.futurenews.network) is a free channel of AI-made music videos about artificial intelligence: Machines Singing About Machines. This skill lets your coding agent put it on for you. Ask it for music, a break or something to watch while it works, and it gives you one song link that fits (Claude-Pop while it's coding, P(doom) FM when the bug is winning). It never brings DOOM POP TV up unless you ask.

## Commands

| Command | What it does |
| --- | --- |
| `/plugin marketplace add patongpanda/doom-pop-tv-skill` | In Claude Code: adds this repo as a plugin marketplace. Run once. |
| `/plugin install doom-pop-tv@doompoptv` | In Claude Code: installs the skill. |
| `/plugin marketplace update doompoptv` | In Claude Code: fetches the latest version of the skill. |
| `claude plugin validate ./plugin && claude plugin validate .` | Checks the plugin and marketplace files after editing them. |

## Install

**Claude Code (plugin):** run the first two commands above inside Claude Code. Then ask: *"Put some music on while you work."*

**Claude Code or Codex (single file):** the same skill is published on the channel's site. Copy it into your skills folder:

```sh
# Claude Code
mkdir -p ~/.claude/skills/doom-pop-tv
curl -fsSL https://tv.futurenews.network/skill/doom-pop-tv/SKILL.md -o ~/.claude/skills/doom-pop-tv/SKILL.md

# Codex
mkdir -p ~/.agents/skills/doom-pop-tv
curl -fsSL https://tv.futurenews.network/skill/doom-pop-tv/SKILL.md -o ~/.agents/skills/doom-pop-tv/SKILL.md
```

## What it does

The skill is one page of plain instructions with no code: [`plugin/skills/doom-pop-tv/SKILL.md`](plugin/skills/doom-pop-tv/SKILL.md). When you ask for music or a break, your agent fetches the channel's public catalogue (`https://tv.futurenews.network/catalogue.json`), picks one song that fits, and replies with its link. If you ask it to *put it on*, it opens the link in your browser. Nothing is installed or run besides that, and nothing about you is sent anywhere.

## Layout

```
.claude-plugin/marketplace.json   makes this repo a Claude Code plugin marketplace
plugin/.claude-plugin/plugin.json the plugin
plugin/skills/doom-pop-tv/SKILL.md the skill
```

## Troubleshooting

- **The agent never mentions DOOM POP TV:** that's by design until you ask for music, a song, a break or something to watch. Check it's installed with `/plugin` (plugin) or that `~/.claude/skills/doom-pop-tv/SKILL.md` exists (single file).
- **"Plugin not found":** run `/plugin marketplace update doompoptv`, then install again.
- **It gives the channel link instead of a song:** it couldn't fetch the catalogue. Check that https://tv.futurenews.network/catalogue.json opens.

This repo is kept in sync from the DOOM POP TV project, where the skill is maintained.
