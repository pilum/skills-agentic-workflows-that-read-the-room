---
name: update-github-info
description: Refresh Mona's GitHub Info website content from official GitHub sources.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
strict: true
engine:
  id: copilot
  copilot-sdk: true
tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    max: 1
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

Read `notes/mona-notes.md` using the GitHub repository tools before drafting any
content. Web fetch the latest content from:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Use the official GitHub Blog and Changelog pages to identify practical,
developer-focused updates that fit Mona's editorial angle. Keep summaries short,
mention the source for every update, and update `site/content/github-info.md`
without removing its existing useful guidance.

After editing the file, use the safe output to open a pull request containing
only the update to `site/content/github-info.md`. The pull request is for Mona
to review; do not write changes directly to the default branch. If there are no
useful updates, do not make a change or open an empty pull request.
