# DevSphere

> **Build. Learn. Belong.** A responsive landing page for a fictional, student-led, GDG-inspired developer community in Gorakhpur, India.

**Disclaimer:** DevSphere is a fictional concept. It is not an official Google Developer Group and is not affiliated with Google. Contact details and social links are demo placeholders.

## Features
- Single self-contained `index.html` (embedded CSS + JS, no build step)
- Sticky navbar with smooth scrolling, active-section highlight, and mobile menu
- Dark / light mode toggle (remembers choice, respects system preference)
- Project category filters, live search, and a details dialog
- Next-event countdown, event-type filters, "Add to calendar" (.ics) download
- Email follow form with validation, copy-email button, back-to-top, scroll progress bar
- Event cards with a working demo registration dialog
- FAQ accordion, animated statistics, scroll reveal
- Accessible: semantic HTML, skip link, visible focus, ARIA labels, reduced-motion support

## Run locally
Open `index.html` in a browser, or serve the folder:
```bash
python3 -m http.server 8000
```

## Deploy to GitHub Pages
1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.

## Tech
HTML, CSS, vanilla JavaScript. Fonts: Space Grotesk and DM Sans (Google Fonts, with system fallbacks).

## License
MIT. See [LICENSE](LICENSE).

## Email OTP verification
Joining and event registration ask for a name and email, then a 6-digit code sent by email (valid 5 minutes, 5 attempts, 30-second resend cooldown).

- **Demo mode (default):** no email is sent. The code is shown inside the dialog so the flow can be tried without a backend.
- **Real emails:** create a free [EmailJS](https://www.emailjs.com/) account, add an email service, and a template that uses the variables `{{to_email}}`, `{{to_name}}`, `{{otp_code}}` and `{{event_name}}`. Then fill in `MAIL` near the bottom of `index.html`:
  ```js
  const MAIL={serviceId:'service_xxx',templateId:'template_xxx',publicKey:'YOUR_PUBLIC_KEY'};
  ```
  Add your site's domain to EmailJS's allowed origins.
- **Security note:** the code is generated and checked in the browser, so it is a UX demo, not real protection. For production, generate, store and verify codes on a server.

## Click sounds
Buttons and links make a soft, short "tok", filter chips play a gentle marimba-style note, and verification plays a small rising chime or a low soft bonk. All sounds are synthesized in the browser with the Web Audio API (no audio files). The speaker button in the navbar mutes them and remembers your choice.
