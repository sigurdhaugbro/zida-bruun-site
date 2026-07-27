# Zida Bruun — artist site

Warm/earthy gallery site with a self-service editing screen for the artist,
built with Decap CMS + Netlify Identity. No coding needed after setup.

Everything in this folder (including sample artworks, using public-domain
historical paintings as image placeholders and Lorem Ipsum body text) is
demo content — replace it once the real site is live.

## One-time setup (you do this)

1. **Push this folder to a new GitHub repository.**
   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin <your-new-repo-url>
   git push -u origin main
   ```

2. **Create the Netlify site from that repo.**
   Netlify dashboard → "Add new site" → "Import an existing project" →
   pick the repo. Build command: leave blank. Publish directory: `.`
   (already set in `netlify.toml`). Deploy.

3. **Turn on Identity.**
   Site settings → Identity → "Enable Identity".

4. **Turn on Git Gateway.**
   Identity → Services → Git Gateway → Enable. This is what lets the
   Decap CMS editor commit changes back to GitHub on the artist's behalf.

5. **Set registration to invite-only.**
   Identity → Registration → "Invite only". This keeps random visitors
   from creating editor accounts.

6. **Invite the artist.**
   Identity → Invite users → enter her email. She'll get an email link
   that sets her password and drops her straight into the editor.

That's it — the editing screen lives at `yoursite.netlify.app/admin/`,
and there's a small "Site owner? Edit this site" link in the site footer
that goes straight there.

## What she can edit

- **Site Settings**: name, tagline, portrait photo, bio, education,
  exhibitions, bibliography, email, phone, Instagram, Facebook.
- **Artworks**: add, edit, remove, or mark pieces sold — title, price
  (NOK), medium/dimensions, description, photo.

Every save commits to GitHub and Netlify automatically redeploys
(usually live within about a minute).

## A note on photos

Decap CMS accepts whatever file she uploads as-is — it doesn't resize or
compress. Ask her to keep photos under a few MB (most phone camera
exports are fine); very large files will slow the page down.

## Local structure

```
index.html          the public site (fetches the two JSON files below)
admin/index.html     the Decap CMS editor shell
admin/config.yml     defines what fields she can edit
content/settings.json   site settings + bio content
content/artworks.json   the list of artworks
images/uploads/          where her uploaded photos will land
netlify.toml         tells Netlify what to publish
```
