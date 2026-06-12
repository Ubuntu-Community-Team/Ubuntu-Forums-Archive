---
title: "[Solved] xorg and nVidia ION"
date: 2009-08-04
forum: Hardware
---

### Post by JamieKitson on 2009-08-04
I was having trouble getting x to start on my nVidia ION box, getting errors like "Screen not found". Turns out that the xserver-xorg-video-nv driver that it was trying to use wasn't compatible. I removed this module from my system to get vesa working, compiled nvidia-kernel-source and created an xorg config file to get it using the correct driver.

---

