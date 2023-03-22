---
title: How to test unpublished GitHub action?
date: 2023-03-23
permalink: /posts/2023_03_23_trying-in-dev-github-action
---

### Problem
When developing a new GitHub Action, then you may want to test it continuously without publishing it first. The UI isn't too helpful here.

### Solution
You can easily test your in development GitHub Actions by referring to them (in ``{{repository}}/.github/workflows/deploy.yml`` file) in the following format:

```
uses: {{USER}}/{{REPOSITORY}}@{{SHA}}
```

Here is an example ``deploy.yaml`` file:

```
name: Build and Deploy
on: [push]
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Deploy
        uses: poseen/github-pages-blog-action@959661a660b9bd37e689c795a417a45966a466f3
        with:
          branch: gh-pages # Optional branch for GitHub Pages
```

### Notes
- ``{{SHA}}`` has to be the full SHA

### Further reading
- https://docs.github.com/en/actions
