# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

This is the `wtfbrubs` GitHub profile repository — the special repo whose `README.md` renders on the GitHub profile page at `github.com/wtfbrubs`.

## Files

- `README.md` — GitHub profile page content (Markdown + limited HTML)
- `dashboard.svg` — Custom SVG dashboard widget embedded at the top of the README; replicates the dark-terminal aesthetic of the `nativos-cloud-site` project (dot grid, IBM Plex Mono, `#00FF6A` green / `#F5C400` yellow / `#58A6FF` blue accents, `#141618` card backgrounds, `#1E2124` borders)
- `.github/workflows/snake.yml` — Runs every 12 h to regenerate the contribution snake animation and push it to the `output` branch as `github-contribution-grid-snake-dark.svg`

## Design system (matches nativos-cloud-site)

| Token | Value |
|---|---|
| Background | `#111214` |
| Card bg | `#141618` |
| Card border | `#1E2124` |
| Green accent | `#00FF6A` |
| Yellow accent | `#F5C400` |
| Blue accent | `#58A6FF` |
| Muted text | `#7A808A` |
| Font | IBM Plex Mono |

## GitHub README constraints

GitHub renders `README.md` as sanitised HTML — no external CSS, no `<script>`, no `class=` attributes, and no CSS variables. Allowed techniques:

- **SVG files** committed to the repo and referenced with `<img src="file.svg"/>` — GitHub renders them inline and allows `<animate>`, `<linearGradient>`, `<pattern>`, etc.
- **Inline `style=`** attributes on HTML elements (limited subset)
- External image services: `shields.io`, `github-readme-stats.vercel.app`, `streak-stats.demolab.com`, `github-profile-trophy.vercel.app`, `github-readme-activity-graph.vercel.app`, `readme-typing-svg.demolab.com`, `komarev.com/ghpvc`

When editing `dashboard.svg`, keep all styles inline — no `<style>` blocks referencing external fonts will work reliably; use generic fallback stacks like `'IBM Plex Mono', 'Courier New', monospace`.

## Common tasks

**Preview the SVG locally:**
```bash
xdg-open dashboard.svg   # Linux
```

**Validate SVG structure:**
```bash
xmllint --noout dashboard.svg
```

**Trigger the snake workflow manually:**
```bash
gh workflow run snake.yml
```

**Push changes to GitHub (profile updates live immediately):**
```bash
git add README.md dashboard.svg
git commit -m "feat: ..."
git push
```
