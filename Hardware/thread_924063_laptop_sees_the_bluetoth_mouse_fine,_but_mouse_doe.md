---
title: "laptop sees the bluetoth mouse fine, but mouse does not work"
date: 2008-09-19
forum: Hardware
---

### Post by srossnz on 2008-09-19
Probably a dumb noob mistake.  Anyway I used blueman and bonded my mouse.. i go into bluetooth settings and input devices and there is my mouse listed "Microsoft Bluetooth Notebook Mouse 5000" so it appears to 'see' it but the mouse does not work at all.  when i dual boot into XP it works fine.  Thanks for any help!

---

### Post by IntuitiveNipple on 2008-09-19
Which version of Blueman is that? There's a complex and as-yet unsolved issue with v0.6* having this problem and also causing kernel panics.

For now maybe disable Blueman loading via System > Preferences > Sessions (if it is listed there) and then re-enable "Bluetooth Manager" (if it is disabled).

---

