# Scam Hai Kya?

Paste an internship post. Get the red flags, a sus score out of 100, and a rubber stamp you can screenshot into the group chat.

Built because every internship hunt in India ends up with a few posts that are really a registration fee, a sales job, or a "PPO of 15 LPA" attached to an unpaid role. This tool spots those patterns in seconds, highlights the exact phrases, and tells you what to ask the recruiter.

**Everything runs in your browser.** No backend, no API calls, no accounts. Whatever you paste never leaves the page.

## What it does

- **Red-flag scan.** 13 pattern rules run on the pasted text and the optional fields (stipend, PPO, applicants, openings). Matches are highlighted in the post with numbered badges.
- **Verdict stamp.** LEGIT-ISH, KINDA SUS, LIKELY SCAM or SCAM, delivered by an animated rubber stamp. A verdict buddy reacts to the result.
- **Live reactions.** The mascot and sus-meter update as you type or paste.
- **Case file.** A breakdown of where the points came from, questions to ask the recruiter (with a copy-as-message button), and next steps that change with the verdict.
- **Share card.** One click makes a 1080x1350 PNG of the verdict for WhatsApp or Instagram.
- **Field guide and sample tickets.** Every rule explained with an example you can try, plus six ready-made sus posts.

## How scoring works

Each rule that matches adds its points. Green flags (a clearly stated stipend, named tools, mentorship) subtract up to 12. The score is clamped to 0 to 100. Any request for money sets a floor of 80, because no legitimate internship charges you.

| Red flag | Points |
| --- | --- |
| They want money from you | +45 |
| Sales job wearing an intern costume | +20 |
| Unpaid or tiny pay, huge PPO promise | +20 |
| Stipend and PPO do not add up | +15 |
| Pressure tactics | +15 |
| "Fresher" who needs years of experience | +15 |
| Hiring through Gmail or WhatsApp | +15 |
| Free work disguised as a task | +15 |
| Paid in "exposure" | +14 |
| Absurd applicants per opening | +12 |
| Salary range wide enough to park a truck in | +12 |
| Buzzword soup | +12 |
| No actual work described | +10 |

Green flags: stipend is stated clearly, concrete tools or projects named, mentorship, reviews or demos mentioned.

Verdict bands: 0 to 19 LEGIT-ISH, 20 to 39 KINDA SUS, 40 to 64 LIKELY SCAM, 65 to 100 SCAM.

## Limits (read this)

This is pattern matching, not machine learning, and it is tuned for English-language Indian internship posts. It will miss clever scams and can flag honest posts that happen to use buzzwords. Treat the stamp as a nudge, not a ruling. Always check the company yourself: LinkedIn, reviews, and the MCA website. If you have already paid a scammer in India, call 1930 or report at cybercrime.gov.in.

## Run it

It is a single HTML file with no build step and no dependencies.

```bash
# just open it
open index.html            # macOS (use xdg-open on Linux, start on Windows)

# or serve it
python3 -m http.server 8000
```

Fonts (Bagel Fat One, Bricolage Grotesque, Permanent Marker) load from Google Fonts, with system fallbacks if you are offline.

## Add or tune a rule

Rules live in the `RULES` array in `index.html`. Each one has an id, a weight, a title, a one-liner, an explanation, and a `find` function that returns whether it matched and which character spans to highlight.

```js
{id:'urgent', w:15, title:'Pressure tactics',
  snark:'Real jobs do not expire in four minutes.',
  why:'Fake urgency is there to stop you from checking the company.',
  find:rx(/urgent(?:ly)?|apply (?:immediately|now)|last date today/gi)}
```

If you add a rule, also add an example sentence to the `EX` object so it shows up in the field guide with a working "Try it" button.

## Built with

Vanilla HTML, CSS and JavaScript, plus the Canvas API for the repelling dot background and the share card. Vibe-coded in a weekend with Claude.

## License

Code is MIT (see `LICENSE`). The character art and clips are third-party and are not covered by that license (see `NOTICE.md`).
