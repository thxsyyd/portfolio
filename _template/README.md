# Portfolio structure

One repo, one folder per job application. Pages never link to each other —
a recruiter for role A must not be able to discover that you also applied to B.

```
portfolio/
├── assets/
│   ├── base.css              shared styling for every page
│   └── photo.jpg             shared portrait
├── _template/                this folder — not published (leading "_")
│   ├── index.html            starting point for a new page
│   ├── FACTS.md              verified fact bank
│   └── README.md             this file
├── academic-coordinator/     live
└── gls-ambassador/           live
```

Root has no `index.html` on purpose: `thxsyyd.github.io/portfolio/` returns 404,
so the only way to reach a page is with its full URL.

## Starting a new application

```bash
cd ~/portfolio
cp -r _template role-slug
```

Use a short, neutral slug — it becomes the public URL
(`thxsyyd.github.io/portfolio/role-slug/`). Then open `role-slug/index.html`
and edit only the blocks marked `<!== EDIT ==>`. Do not add a `<style>` block.

Preview before pushing:

```bash
cd ~/portfolio && python3 -m http.server 8899
# then open http://localhost:8899/role-slug/
```

Publish:

```bash
git add -A && git commit -m "Add <role> application page" && git push
```

GitHub Pages rebuilds in about a minute.

## The three layers

| Layer | Where | How often it changes |
|---|---|---|
| Styling | `assets/base.css` | never, unless restyling everything |
| Facts | timeline + contact blocks, `FACTS.md` | only when the CV changes |
| Role | everything marked `EDIT` | every application |

Only the third layer is real work. The bulk of it is the Role Fit table:
one row per requirement quoted from the posting, each with concrete evidence,
and honest `adjacent` tags on the gaps.

## Keeping pages consistent with the resume

The "Experience at a Glance" timeline must match the resume exactly — same
titles, same dates, same honours. When the resume changes, update every live
page's timeline, not just the newest one.
