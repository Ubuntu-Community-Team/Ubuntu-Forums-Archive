---
title: "Configure tridentfb"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by digge on 2007-05-28
Hi all

Im trying to get tridentfb driver to default to a 1024x768 16bpp console during boot. But seems no matter what options i pass to the kernel i still end up in 640x480 8bpp. 

dmesg shows me the driver is getting loaded and it detects my screen and videoram correctly. After bootup i can change the resolution using fbset so the driver does work just wont default to the correct resolution.

Im trying to get this to work on my Toshiba laptop Satellite S1800-204, it has a trident CyberBlade i1. Hope someone can shed some light on the very cryptic manpages of tridentfb and modedb ;)

//DiGGe

---

