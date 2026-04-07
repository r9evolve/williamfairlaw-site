# Law Offices of William E. Fair — Static Site

Revamped static HTML site for williamfairlaw.com. Zero monthly cost — hosted on GitHub Pages.

## File Structure

```
williamfairlaw/
├── index.html       ← Home
├── about.html       ← About Us
├── services.html    ← Services
├── faqs.html        ← FAQs
├── style.css        ← All styles
├── main.js          ← Nav, FAQ accordion, form handler
├── CNAME            ← Custom domain for GitHub Pages
└── README.md
```

---

## One-Time Setup

### 1. Set up contact form (5 min, FREE)

1. Go to [formspree.io](https://formspree.io) and sign up free
2. Create a new form, set destination email to `closings@wfairlaw.com`
3. Copy your Form ID (looks like `xabcdefg`)
4. In `index.html`, find this line and replace `YOUR_FORM_ID`:
   ```html
   <form id="contact-form" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```
5. Free plan allows 50 submissions/month — upgrade to $10/mo for unlimited

### 2. Push to GitHub

```bash
cd williamfairlaw
git init
git add .
git commit -m "Initial site launch"
# Create a repo at github.com then:
git remote add origin https://github.com/YOUR_USERNAME/williamfairlaw-site.git
git branch -M main
git push -u origin main
```

### 3. Enable GitHub Pages

1. Go to your repo on GitHub
2. Settings → Pages
3. Source: `Deploy from a branch`
4. Branch: `main`, folder: `/ (root)`
5. Click Save
6. Your site will be live at `https://YOUR_USERNAME.github.io/williamfairlaw-site` in ~2 min

### 4. Point GoDaddy DNS to GitHub Pages

In GoDaddy DNS Manager, delete existing A records and add these 4:

| Type | Name | Value              | TTL |
|------|------|--------------------|-----|
| A    | @    | 185.199.108.153    | 1hr |
| A    | @    | 185.199.109.153    | 1hr |
| A    | @    | 185.199.110.153    | 1hr |
| A    | @    | 185.199.111.153    | 1hr |
| CNAME | www | YOUR_USERNAME.github.io | 1hr |

Then in GitHub Pages settings, enter `williamfairlaw.com` under Custom Domain and check **Enforce HTTPS**.

DNS propagation: 15 min – 24 hrs.

---

## Images

The site currently loads images directly from the current WordPress server.
Once you decommission WordPress hosting, download these files and add them to an `images/` folder:

| File | URL |
|------|-----|
| hero-bg.jpg | https://williamfairlaw.com/wp-content/uploads/2019/11/iStock-9245202321.jpg |
| cta-bg.jpg | http://williamfairlaw.com/wp-content/uploads/2019/11/iStock-629098988.jpg |
| about-team.jpg | https://williamfairlaw.com/wp-content/uploads/2019/11/iStock-850906706-800x600.jpg |
| services-card.jpg | https://williamfairlaw.com/wp-content/uploads/2019/11/iStock-9245202321-800x600.jpg |
| faqs-card.jpg | https://williamfairlaw.com/wp-content/uploads/2019/11/iStock-1133687413-800x600.jpg |

After downloading, update `style.css` (hero-bg and cta-band `background-image` URLs)
and `index.html` / `about.html` `<img src="...">` tags to use local paths like `images/about-team.jpg`.

---

## Updating Content

Everything is plain HTML — open any `.html` file in any text editor to change text.
To deploy changes: `git add . && git commit -m "Update content" && git push`

GitHub Pages auto-deploys within ~60 seconds of each push.

---

## Cost Summary

| Item | Cost |
|------|------|
| GitHub Pages hosting | **$0/mo** |
| SSL certificate | **$0** (auto via GitHub) |
| Domain (GoDaddy, keep existing) | ~$20/yr |
| Contact form (Formspree free tier) | **$0** (50 submissions/mo) |
| **Total** | **~$0/month** |
