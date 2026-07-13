# How to edit your portfolio site

Everything lives in **one file — `index.html`** — plus images in `assets/img/`.
Open `index.html` in any text editor (Notepad works; [VS Code](https://code.visualstudio.com/) is nicer).
To preview: double-click `index.html` — it opens in your browser. Maps and fonts need internet.

---

## 1. Edit text

Press `Ctrl+F` in your editor, search for the sentence you want to change, edit it, save,
then refresh the browser. That's it — headings, project copy, the About story, everything is plain text in `index.html`.

## 2. Change your tagline / hero

Search for `hero` — the name, role line, tagline and the two-sentence positioning statement are together
near the top of the `<body>`.

## 3. Add or swap an image

1. Put the image in `assets/img/` (keep it under ~300 KB — resize to ~1400 px wide max; [squoosh.app](https://squoosh.app) is an easy compressor).
2. Reference it where you want it. Inside a case-study dialog, copy an existing figure block:

```html
<figure class="fig">
  <img src="assets/img/YOUR-IMAGE.jpg" alt="Describe the image for screen readers" width="1400" height="900" loading="lazy">
  <figcaption>One-line caption.</figcaption>
</figure>
```

Set `width`/`height` to the image's real pixel size (right-click the file → Properties → Details).

## 4. Add a new project card

Each project is two pieces: a **card** (in the `<section id="projects">` area) and a **dialog**
(the pop-up case study, near the bottom of the file, look for `<dialog class="case" ...>`).

1. Copy an existing `<button class="mini-card" ...>` block (or a big `<button class="card" ...>` for a featured project) and edit its text.
2. Copy an existing `<dialog class="case" id="case-something">...</dialog>` block and edit its content.
3. Make the card's `data-dialog="..."` match the dialog's `id="..."`. The click wiring is automatic.

## 5. Add a pin to a map

Search for `SITES` in the `<script>` at the bottom. Each pin is one line:

```js
{ll:[22.383,113.955],name:"Tsing Shan, Tuen Mun — training region",kind:"train"},
```

`ll` is [latitude, longitude] (right-click any spot in Google Maps to copy these).
`kind:"train"` = solid dot, `kind:"field"` = hollow dot.

## 6. Change colors / theme

All colors are variables at the top of the `<style>` block — `--accent` is the terracotta;
`:root[data-theme="dark"]` and `:root[data-theme="light"]` hold the two themes.

## 7. Update links / email

Search for `waikin1028@gmail.com`, `github.com/waikinli98`, or `linkedin.com` — each appears in
the visible page and once in the JSON-LD block near the top (used by search engines).

## 8. Bring back the "Download CV" button (currently removed)

Save your CV as `assets/KennethLi_CV.pdf`, then add this line back inside the hero's
`<div class="cta-row">` (between the "View projects" and "Contact" buttons) in `index.html`:

```html
<a class="btn btn-ghost" href="assets/KennethLi_CV.pdf" download>Download CV</a>
```

---

## Publish your changes to the live site

After editing, run these three commands in this folder
(right-click the folder in Explorer → **Open in Terminal**):

```
git add -A
git commit -m "Describe what you changed"
git push
```

The live site at https://waikinli98.github.io/ updates in about a minute.

## If something breaks

Run `git log --oneline` to see your history, and
`git checkout -- index.html` to throw away uncommitted changes and return to the last working version.
