---
title: "nVidia drivers not in use"
date: 2010-05-14
forum: Hardware
---

### Post by hellrazor236 on 2010-05-14
Well, I managed to get my PC to a friend's house and connect to the internet (I'm using it right now :)), and I managed to install **nvidia-current**, **nvidia-kernel-common**, **nvidia-settings** and the 2 **xserver-xorg-video-randomcrap** packages.

I restarted just to make sure it'd all work properly, and my screen is off-center (looks like they should be working), but when I go to Preferences > Hardware Drivers it says "This driver is activated but not currently in use", and when I try to go into Preferences > NVIDIA X Server Settings it tells me that I'm not running the NVIDIA X Driver. Any help?

---

### Post by ShawnDBruce on 2010-05-14
Try opening a terminal and typing: sudo nvidia-xconfig

Hope that helps

---

