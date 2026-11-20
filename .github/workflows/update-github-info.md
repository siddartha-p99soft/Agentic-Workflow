---
name: update-github-info
description: Propose concise, sourced updates to the GitHub Info page for Mona's review.
intent: Keep the GitHub Info page useful and current with practical, officially sourced GitHub guidance.
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
  copilot-requests: write
strict: true
network:
  allowed:
    - github.blog
    - github.com
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit: true
  web-fetch: {}
safe-outputs:
  create-pull-request:
    title-prefix: "[GitHub Info] "
    draft: false
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

Read `notes/mona-notes.md` and `site/content/github-info.md` first. Use the `web-fetch` tool to read both:

- https://github.blog/latest/
- https://github.blog/changelog/

Identify recent items that provide practical value to GitHub developers and fit the page's existing themes. Keep any summaries short, avoid duplicating content already on the page, and include a direct source link for every addition based on the GitHub Blog or Changelog. Make changes only to `site/content/github-info.md`, preserving its existing editorial angle and structure.

If neither source has a sufficiently useful, non-duplicative item, or the page would not benefit from a change, make no edits and use `noop` with a brief reason. Otherwise, create a pull request containing only the page update, with a concise explanation of the selected items and sources, for Mona to review. Never write directly to the default branch or use any other write path.
