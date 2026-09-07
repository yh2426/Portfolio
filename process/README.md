# Process Log

A minimal, self-hosted daily/weekly process-documentation site for TETL Fall 2026 — visually distinct from the main portfolio on purpose (raw/journal look, not the polished case-study style), and lives at a quiet URL under your existing site rather than in the main nav.

## Structure

```
process/                (rename this folder to `process` when you drop it into Portfolio)
  index.html      the page itself (don't need to touch this normally)
  style.css       visual style (journal/notebook look)
  entries.js      <-- this is the file you edit every time you log something
  assets/
    2026-09-06/   put that day's images/videos in a folder named by date
```

## Adding a new entry

1. Drop any photos/videos for the day into a new folder under `assets/`, named by date, e.g. `assets/2026-09-13/`.
2. Open `entries.js` and add a new object to the `entries` array (copy-paste this template and fill it in):

```js
{
  date: "2026-09-13",
  title: "Short title for the day",
  tags: ["sketch", "prototype"],
  body: "What happened. What you tried. What didn't work.\n\nSecond paragraph if you want one.",
  media: [
    { type: "image", src: "assets/2026-09-13/post-it-wall.jpg", caption: "brainstorm, round 1" },
    { type: "video", src: "assets/2026-09-13/test-clip.mp4", caption: "first working test" }
  ]
}
```

3. Save, commit, push. That's it — no build step.

Order in the array doesn't matter (the page sorts by date automatically), but adding new entries at the top keeps the file easy to read yourself.

## Publishing as a quiet subpage of your existing portfolio

Since this is plain static HTML/CSS/JS with no build step and only relative paths, it works as a subfolder inside your existing `Portfolio` repo regardless of what that site is built with — a real file at a real path always wins over whatever routing the rest of the site uses.

1. In your local clone of the `Portfolio` repo, copy this whole folder in and rename it `process`, so you end up with:
   ```
   Portfolio/
     (your existing site files...)
     process/
       index.html
       style.css
       entries.js
       assets/
   ```
2. Commit and push as usual:
   ```bash
   git add process
   git commit -m "add process log"
   git push
   ```
3. It'll be live at **`https://yh2426.github.io/Portfolio/process/`** — not linked from anywhere unless you add a link yourself (see below).

### Adding a quiet entry point (optional)

If you want a way in without putting it in the main nav, the least conspicuous option is a small text line in your site's footer or About page — something like:

```html
<a href="/Portfolio/process/" style="font-size:12px; opacity:0.55; text-decoration:none;">process log</a>
```

Drop that into whatever footer/About component your site already has, adjust the styling to match, and it'll read as a quiet aside rather than a nav item. If your site has no shared footer to hook into, it's just as fine to leave it completely unlinked and hand the URL directly to whoever needs it (e.g. your instructor).

## Updating after that

Every time you log something:
```bash
git add process
git commit -m "log: 2026-09-13"
git push
```
