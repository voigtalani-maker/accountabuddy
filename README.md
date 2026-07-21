# 📚💪 Accountabuddy 💛

A warm, cozy daily-accountability app for two matric buddies — **Alani** and **Buhle** —
to keep each other on track through their final school year. Morning check-ins, evening
reflections, a friendly points game, shared goals, and gentle "nudges" when someone slips.

Built to be opened every day from a phone. Everything syncs in the cloud so each buddy
can see the other's check-ins live. 🌙☕

---

## How to use it

1. Open the app link on your phone.
2. Pick your name and type your password (it's just your **name in lowercase**):
   - Alani → `alani`
   - Buhle → `buhle`
3. **Add to Home Screen** so it feels like a real app and works offline:
   - **iPhone (Safari):** Share button → *Add to Home Screen*.
   - **Android (Chrome):** menu ⋮ → *Install app* / *Add to Home Screen*.
4. Do your **📝 Check-In** in the morning and your **🌙 Evening** questions at night.
5. Every **Sunday**, sit down together and do the **📅 Weekly Review** + **🎯 Goals** check-in.

That's it — no accounts to create, nothing to install on a computer.

---

## What's inside (the tabs)

| Tab | What it's for |
|---|---|
| 🏠 **Home** | Today's status for both of you, this week's points, alerts, next Sunday review |
| 📝 **Check-In** | The full daily form (sleep, study, health, screen time, reflection, plan) |
| 🌙 **Evening** | 5 short accountability questions you can each answer & read each other's |
| 📅 **Weekly** | Auto-calculated stats for the week + your written reflection |
| 🎯 **Goals** | Your shared long-term goals — tick them off together |
| 🏆 **Points** | Daily / weekly / yearly leaderboard between the two of you |
| 💛 **Nudges** | Missed-commitment tracker + the friendly "consequences" list |
| 🤝 **Our Pact** | Your accountability agreement & motto |
| ⚙️ **Settings** | Your personal targets (water, screen-time, gym & study goals) |

---

## Points (how they're earned)

| Activity | Points |
|---|:---:|
| 📚 1 hour studied | +1 per hour |
| 💪 Gym session | +3 |
| 💧 Water goal reached | +1 |
| 🛏 8+ hours of sleep | +2 |
| 📵 Stayed under screen-time goal | +2 |
| 🥗 Healthy eating (3/3 meals) | +2 |
| 🌅 Woke up on time | +1 |
| ⭐ Completed every planned task | +5 |

**Weekly bonuses:** studied every planned day (+10), every planned gym session (+10),
averaged 8+ hrs sleep (+10), under screen goal all week (+10).

---

## 🎨 Want to tweak it yourself, Alani?

Almost everything you'd want to change lives in **one place** near the top of
`index.html`, in a block called **`CONFIG`**. It's clearly commented. For example:

- **Point values** → `CONFIG.points` and `CONFIG.weeklyBonus`
- **Default goal targets** (water litres, screen-time hours, etc.) → `CONFIG.defaultSettings`
- **Subject tags** on the check-in → `CONFIG.subjects`
- **The starter goals** → `CONFIG.seedGoals`
- **The nudge/consequence list** → `CONFIG.consequenceOptions`

The **colours** live just below that, in the CSS `:root` block — change a value like
`--latte` and it updates everywhere in the app.

If you change something and it stops working, just undo your edit and it'll be fine. 💛

---

## For whoever maintains it (the techy bits)

- **One file app:** everything is in `index.html` (HTML + CSS + JavaScript). No build step.
- **Photos** live in `images/`. **Icons**/`manifest.webmanifest`/`sw.js` make it an
  installable PWA that works offline.
- **Cloud sync:** [Supabase](https://supabase.com). Data is stored in one table,
  `aab_state`, as three rows keyed by an `owner` column: `alani`, `buhle`, and `shared`
  (goals + nudges). Each person's device writes its own row and reads all three; changes
  arrive live via Supabase Realtime. The Supabase URL + public key are set in the `SYNC`
  object near the bottom of `index.html`. (The key is a *publishable* anon key — safe to
  ship in the browser.)
- **Offline-first:** edits save to `localStorage` immediately and sync when back online.
- **Hosting:** static files served over HTTPS (e.g. GitHub Pages). No server needed.

### Run it locally
Just open `index.html` in a browser — or serve the folder over http (needed for the
service worker / install to work), e.g. any static file server pointed at this folder.

---

Made with 💛 for matric. *Discipline over motivation. Progress over perfection. Better together.*
