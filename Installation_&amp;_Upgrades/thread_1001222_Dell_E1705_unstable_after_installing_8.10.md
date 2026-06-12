---
title: "Dell E1705 unstable after installing 8.10"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by dmeans on 2008-12-03
The PC is pretty much unusable for anything other than casual web browsing.  Here's the list of problems I'm having with 8.10 (fresh install)

- Keyboard randomly locks up.  Only solution is to logout/login.
- Windows / Desktop / Menu-bar randomly freeze.  Solution: power-down/up.
- Wireless (Intel) unreliable - randomly drops connection.
- VPNC won't stop or re-start after wireless drops and reconnects. vpnc-disconnect will not kill it, kill -9 won't stop it.  Solution: re-boot
- Keyboard auto-repeat and delay cannot be tuned to reasonably low values.
- tsclient will not shut-down once wireless disconnects/reconnects.  Solution is to logout/login
- tsclient leaves artifacts on the desktop, then the desktop freezes.  Solution: logout/login or re-boot.

---

