---
name: update-github-info
description: Keep the GitHub information page current with recent GitHub Blog and Changelog updates.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  copilot-requests: write
engine:
  id: copilot
  copilot-sdk: true
network:
  allowed:
    - defaults
    - github.blog
    - github.com
tools:
  edit:
  web-fetch:
safe-outputs:
  create-pull-request:
    max: 1
    reviewers:
      - mona
---

# Update GitHub Information

Read `notes/mona-notes.md` and `site/content/github-info.md` first. Fetch and review:

- https://github.blog/latest/
- https://github.blog/changelog/

Update `site/content/github-info.md` with relevant, verified information from those sources, guided by `notes/mona-notes.md`. Preserve the existing structure and writing style. Do not invent details, and avoid unrelated changes. If there is nothing substantive to update, do not create a pull request.

When you make changes, use the `create-pull-request` safe output to open one pull request for Mona (`mona`) to review. Summarize the updates and link the sources in the pull request description. Do not write directly to the default branch.