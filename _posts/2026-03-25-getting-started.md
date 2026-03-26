---
layout: post
title: Site scaffold (private reference)
date: 2026-03-25 12:00:00 -0400
description: Cheat sheet for writing posts — not shown on the live site
published: false
---

Personal notes for this repo’s Jekyll / al-folio setup. **`published: false`** means this file stays in Git but is **not** built into the website (no URL, not on the Posts list, not in RSS). Safe to keep as reference.

---

## Post filenames (required)

Posts must live in **`website/_posts/`** and the filename **must** start with a date:

**`YYYY-MM-DD-short-title.md`**

- Use **four-digit year**, **two-digit month**, **two-digit day** (e.g. `2026-03-05`, not `2026-3-5`).
- Without that **`YYYY-MM-DD-`** prefix, Jekyll usually **does not** treat the file as a post.

The slug after the date feeds your URL shape (see `permalink` in `_config.yml`).

---

## Front matter for a public post

Minimum:

```yaml
---
layout: post
title: "Your title"
date: 2026-03-26 14:30:00 -0400
---
```

Then Markdown **below** the closing `---`.

**Optional fields**

- `description:` — short summary on the blog index
- `tags:` — e.g. `tags: [milestone]` or `tags: milestone`. You do **not** need to add every tag to `_config.yml` → `display_tags`; that setting only adds optional filter links at the top of the blog index.
- `author:` — shown as “by …” on the post layout
- `published: true` — default if omitted; use **`published: false`** for drafts you commit but don’t want live yet

---

## Links with GitHub Pages `baseurl`

Use Liquid in the Markdown body so paths work locally and on `username.github.io/repo-name/`:

- Home: `[text]({{ "/" | relative_url }})`
- Blog index: `[text]({{ "/blog/" | relative_url }})`
- File under `assets/`: `[text]({{ "/assets/project/final-report.pdf" | relative_url }})`

---

## Embeds

Raw HTML in the post body (e.g. `<iframe …>` for YouTube) usually passes through. Put the iframe **outside** a fenced code block if you want it to render. Use trusted sources and `https` only.

---

## Preview

From `website/`: `docker compose up`, then open **`http://localhost:8080/<your-baseurl>/`** (see `_config.yml` → `baseurl`).
