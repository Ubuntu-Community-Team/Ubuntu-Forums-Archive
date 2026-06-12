---
title: "PowerMac6,3 LCD Brightness"
date: 2012-11-20
forum: Hardware
---

### Post by awol99 on 2012-11-20
So i have a Lampshade G4 iMac (Powermac6,3) with ubuntu 12.10.

the LAST problem to solve is LCD Brightness. It's cranked to full and i'm going blind.

with Debian 6.0.6 the keyboard brightness keys (F1, F2) work well, and "xdotool key XF86MonBrightnessDown" works also. i'd stick with Debian except it does not support my USB wireless dongle r8712u.

so Brightness CAN be controlled on this hardware. it just seems xorg does not support XF86MonBrightnessDown in ubuntu on this hardware. it's certainly not listed as an option for xdotool.

i'm using the nv driver in xorg.conf for the GeForce-FX-Go5200

the path /sys/class/backlight/ is empty.

any ideas would be welcome.

---

