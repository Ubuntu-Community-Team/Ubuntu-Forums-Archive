---
title: "Autodetect presence of external monitor?"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by robzon on 2007-09-03
Hello,

I have an intel i915 card (using i810 driver) on gutsy, and I've just configured Xinerama to use my external monitor. Everything works great except that if I disconnect my external monitor and restart X, the Xserver doesn't detect that the ext. monitor is not present and I still get wide desktop with bigger part of it inaccessible.
Is there a way to make X autodetect if my external monitor is connected and use Xinerama only in that case? It's extremely annoying to have to replace xorg.conf a few times a day (3D doesn't work with xinerama and I'm moving a lot).

thanks

---

