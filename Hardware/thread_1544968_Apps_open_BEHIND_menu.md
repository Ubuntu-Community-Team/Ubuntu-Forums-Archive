---
title: "Apps open BEHIND menu?"
date: 2010-08-03
forum: Hardware
---

### Post by IanW on 2010-08-03
Just tried installing UNR 10.04 onto my bosses new netbook (at his request).
All went well until we restarted after the install.

Now, opening any application will work fine - for a second or so - then the menu pops up over the app!
Attempting to re-select the app by either clicking on its icon on the top panel or Alt-Tab has the same effect,
the app will appear for about a second, then the menu will pop up once more!] (*,)

Device is a Compaq Mini 311
OS is fresh install of UNR 10.04 with nvidia-current & Broadcom STA drivers, no other updates.

---

### Post by IanW on 2010-08-04
This now seems to be caused by an interaction between netbook-launcher, maximus and nvidia-current.
Possibly a recurrence of bug #[364921]("https://bugs.launchpad.net/ubuntu/+source/maximus/+bug/364921")?

My current workaround is to disable netbook-launcher & maximus in "Startup Applications"

---

