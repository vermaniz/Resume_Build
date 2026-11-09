# Manish Verma – Resume (HTML → PDF)

A one-file, A4-sized resume built as `index.html`. It mirrors the original LaTeX (Overleaf) resume: Bitstream Charter font, same spacing, two pages.

| | |
|---|---|
| **Live site** | https://vermaniz.github.io/Resume_Build/ |
| **Repository** | https://github.com/vermaniz/Resume_Build |
| **Main file** | `index.html` (everything lives in this one file) |

---

## How it works (the big picture)

```
Edit index.html  →  upload/push to GitHub  →  GitHub Pages rebuilds (1–2 min)  →  live site updates  →  Download PDF from the site
```

- GitHub Pages is switched on for the `main` branch, root folder. Every new commit to `main` republishes the site automatically.
- The Charter font is embedded inside `index.html`, so the resume looks the same on every device.
- **Do not edit the long `@font-face` lines at the top of the file.** They hold the embedded font.

---

## Part 1 – Make a change

Pick **one** of the three methods. Method A is the easiest.

### Method A – Edit on your computer, upload through the GitHub website (no git needed)

1. Open `index.html` in VS Code (the copy in `Desktop\My Folder\Resume_Build`).
2. Make your change (see **Part 4 – What to edit** below) and save with `Ctrl+S`.
3. Double-click `index.html` to open it in Chrome or Edge, and check it. Press `F5` after each edit.
4. Open this link while logged in to GitHub as **`vermaniz`**:
   `https://github.com/vermaniz/Resume_Build/upload/main`
5. Drag `index.html` onto the page.
6. Scroll down, type a short message such as `Update experience`, and click **Commit changes**.
7. Go to **Part 2** to check the live site.

> Uploading a file with the same name replaces the old one. GitHub keeps the old version in its history.

### Method B – Use VS Code and git (clone, edit, push)

Use this if you want proper version history from VS Code.

**One-time setup**

1. Install **VS Code** (https://code.visualstudio.com) and **Git** (https://git-scm.com).
2. In VS Code press `Ctrl+Shift+P`, type `Git: Clone`, and paste:
   `https://github.com/vermaniz/Resume_Build.git`
3. Choose an **empty** folder to clone into, then click **Open**.
4. Make sure you are signed in to GitHub as **`vermaniz`** (the Accounts icon, bottom-left of VS Code).
   If VS Code is signed in as a different account, the push fails with a **403 permission denied** error. See **Part 5 – Troubleshooting**.

**Every time you want to change something**

1. Open the cloned folder in VS Code and edit `index.html`.
2. Save with `Ctrl+S`, then open the file in a browser and check it.
3. In VS Code open **Source Control** (branch icon in the left bar).
4. Click `+` next to `index.html` to stage it.
5. Type a message such as `Update skills` and click **Commit**.
6. Click **Sync Changes** (or **Push**).
7. Go to **Part 2** to check the live site.

> If you ever see "refusing to merge unrelated histories", don't force it. Clone into a fresh empty folder (step 2–3 above) and copy your latest `index.html` into it.

### Method C – Edit directly on the GitHub website (small text fixes only)

1. Open https://github.com/vermaniz/Resume_Build and click `index.html`.
2. Click the **pencil icon** (Edit this file) at the top right of the file.
3. Use `Ctrl+F` inside the editor to find the text you want to change, and edit it.
4. Click **Commit changes…**, add a message, and click **Commit changes**.
5. Go to **Part 2**.

> This works for a typo or a date. For bigger edits use Method A. The file has a large embedded font, which makes the web editor slow.

---

## Part 2 – Check the live site

1. Open the **Actions** tab on GitHub. Wait until the latest **pages build and deployment** run shows a green tick (about 1–2 minutes).
2. Open https://vermaniz.github.io/Resume_Build/
3. Press `Ctrl+F5` to force a fresh load. The browser may still be showing the old copy.
4. Check your change. Open the site on your phone or another computer if you want a second check.

---

## Part 3 – Download the PDF

1. Open the live site (or your local `index.html`) in **Chrome or Edge on a laptop or desktop**.
2. Click **⬇ Download PDF** at the bottom of the page.
3. In the print dialog set:
   - **Destination:** Save as PDF
   - **Paper size:** A4
   - **Margins:** **Default** (not "None", or the page-2 top margin disappears)
   - **Background graphics:** on
4. Click **Save**.
5. Open the PDF and check:
   - two pages, with only "Languages Known" on page 2
   - icons are navy
   - the email, LinkedIn and website links work when clicked

> Phones handle the print dialog differently. Make the final PDF on a laptop or desktop.

---

## Part 4 – What to edit in `index.html`

Open the file and press `Ctrl+F` to search for a comment such as `<!-- Experience -->` to jump to a section.

**Change text:** edit the words between the tags. Write `&amp;` for "&" and `&ndash;` for "–".

**Add or remove a bullet** (Experience, Education, Accomplishments):

```html
<li>Your new bullet text.</li>
```

**Add or remove an item in Skills, Software Proficiency or Languages Known** (the 3-column grids):

```html
<div class="col-item">New skill</div>
```

**Add another job or degree:**

```html
<div class="two-col">
  <div class="tc-left"><strong>Job Title</strong>, Company &ndash; City</div>
  <div class="tc-right">Jan 2024 &ndash; Present</div>
</div>
<ul class="cv-bullets">
  <li>Bullet</li>
</ul>
```

**Add a whole new section:**

```html
<div class="cv-section">
  <h2>Section Title</h2>
  <ul class="cv-bullets">
    <li>Item</li>
  </ul>
</div>
```

**Remove a section:** delete everything from its `<div class="cv-section">` to the matching `</div>`.

**Bold / italic inside text:** `<strong>bold</strong>` and `<em>italic</em>`.

**Header contact line** (under `<!-- Header -->`): each item is an icon plus a link.
- Change a link by editing `href` (`mailto:…` for email, `tel:+91…` for phone, `https://…` for websites).
- Change the visible text by editing the text after the `</svg>`.
- To remove an item, delete its `<a>…</a>` and the `<span class="sep">|</span>` just before it.
- Icon colour: `fill: #14285a;` in the `.contact-item svg` rule.
- If the row gets too wide, lower `font-size: 8.5pt;` in the `.cv-contact` rule.

**Force a page break before a section:** add `style="break-before: page"` to its `<div class="cv-section">`.

**Careful:** if you delete a closing tag such as `</div>` or `</li>` by accident, the layout can break. Press `Ctrl+Z` to undo, and always check in the browser before uploading.

---

## Part 5 – Troubleshooting

| Problem | What to do |
|---|---|
| Push says **403 permission denied to `vermamwest`** | VS Code / git is logged in as the wrong GitHub account. Either use Method A (upload on the website, logged in as `vermaniz`), or give that account write access under **Settings → Collaborators** in the repo, or sign in as `vermaniz`. |
| Live site still shows the old version | Wait 1–2 minutes, check the **Actions** tab for a green tick, then press `Ctrl+F5`. |
| Actions run shows a red cross | Open the run and read the error. Make sure `index.html` is in the `main` branch root and Pages is set to **Deploy from a branch → main → / (root)** under **Settings → Pages**. |
| Layout broke after an edit | Undo with `Ctrl+Z`, or restore the previous version: open `index.html` on GitHub → **History** → pick an older commit → **Raw** / download it. |
| Header contact row wraps to 2 lines | Lower the `.cv-contact` font size slightly, or shorten the text. |
| PDF has no top margin on page 2 | In the print dialog set Margins to **Default**, not "None". |
| PDF has the wrong page size | In the print dialog set Paper size to **A4**. |

---

## Notes

- The repository is **public**. Anyone with the link can see the resume, including the email and phone number.
- Keep a backup copy of `index.html` somewhere outside the repo before making big changes.
- The site only needs `index.html`. This README is for you and does not appear on the resume page.
