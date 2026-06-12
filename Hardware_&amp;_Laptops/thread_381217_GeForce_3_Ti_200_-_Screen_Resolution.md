---
title: "GeForce 3 Ti 200 - Screen Resolution"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by bmartin on 2007-03-10
I'm running Ubuntu on a 15" LCD Monitor with a GeForce 3 Ti 200 video card using the legacy Nvidia drivers (installed via EasyUbuntu).

I've messed around with my xorg.conf file, changing it so that only the "24-bit 1024x768" display option is available.

X doesn't seem to care. No matter what values I put in, the monitor displays 800x600 @ 50 Hz. I've tried setting the values manually using **dpkg-config xserver-xorg**; there seems to be no difference. I know the monitor supports 1024x768... and even if it didn't, X should have failed to start. It's like X is ignoring my xorg.conf file.

Any ideas as to what's going on? Do Nvidia's legacy drivers not support resolutions greater than 800x600?

---

### Post by bmartin on 2007-03-10
Strangely, that monitor/card combo didn't want to play nicely together. I swapped the card with the GeForce 5700 in my other PC and both PCs were happy. It seemed to solve both of the problems.

---

