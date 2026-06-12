---
title: "Buggy Driver?"
date: 2009-10-30
forum: Hardware
---

### Post by xaenyx on 2009-10-30
OK, I have a wireless card: WPC11 v4.0, based on a Realtek chipset.  I previously used the card in another laptop, and it worked fine (under 8.04).  I put it into an n610c laptop, and it no longer works...  

When I plugged it in, it was detected and installed with the rtl8180 driver.  It would detect networks and connect to mine at 94% signal strength, but immediately afterwards it would drop to 4%, and then disconnect.  It would then spend the next 15 minutes trying to re-connect, but never succeeding, and eventually stopping altogether.

So, I downloaded the winXP driver (which works perfectly under XP or Windows 7 on the same computer), and ndiswrapper, and installed the former with the latter and blacklisted rtl8180.  The card was detected and installed, but the problem persists.

Any idea what is going on?

---

### Post by xaenyx on 2009-10-30
bump

---

### Post by xaenyx on 2009-10-30
I looked in /var/log/messages, and it says the link was established.  Afterwards, every 6 seconds or so, there is a line reading:

ndiswrapper (mp_reset:64): wlan0 is being reset

---

### Post by xaenyx on 2009-10-31
bamp

---

