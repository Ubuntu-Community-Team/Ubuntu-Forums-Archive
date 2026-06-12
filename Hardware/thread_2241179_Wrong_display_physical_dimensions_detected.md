---
title: "Wrong display physical dimensions detected"
date: 2014-08-24
forum: Hardware
---

### Post by spectatorx on 2014-08-24
Lubuntu 14.04 amd64, kernel 3.17rc1, gigabyte radeon r7 260x 1GB, amd catalyst 14.6rc, display connected via hdmi cable.

As display, atm, i'm using 37" samsung tv which has real physical dimensions 984 x 572 mm but here is output of xdpyinfo | grep -B2 resolution :
screen #0:
  dimensions:    1920x1080 pixels (508x285 millimeters)
  resolution:    96x96 dots per inch


I want to set proper physical dimensions which will help me with too low dpi.

Concluding:
how to set real physical dimensions?


Ok, i've already figured out that i can change it with this command:
xrandr --fbmm 984x572
but after reboot i get previous settings back, so now things are a bit changed and the problem is....
how to keep changes?

---

