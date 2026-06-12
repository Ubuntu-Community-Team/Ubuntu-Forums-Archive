---
title: "Resolution limited on an old Gericom"
date: 2011-12-18
forum: Hardware
---

### Post by IcyTotem on 2011-12-18
I wanted to install ubuntu on this old Gericom Hummer 2640e XL. I tried to install Ubuntu 8.04, but could not go past the black screen at the start (sometimes the monitor even turned off). Reconfiguring X didn't work. Changing grub starting options didn't work. I couldn't install proprietary drivers because they do not exist. The graphics card is an Intel Extreme Graphics, 64MB (82845G/GL), currently using i915.
So I decided to reinstall a newer, and maybe lighter, version of Ubuntu and went for Lubuntu, which currently has a 3.0.0.13-generic kernel. With this, I ended up having a resolution of 640x480 every time I booted. Creating a new resolution profile and applying it with xrandar brough no results. I do not remember the detailed exception I was received, but it was about not being able to apply a configuration... Manually adding lines in the desktop environment configuration file didn't work.

xrandr outputs:
```
Screen 0: minimum 320x320, current 640x480, maximum 2048x2048
VGA1 unknown connection (normal left inverted right x axis y axis)
   1360x768 59.8
   ...
   640x480 59.9
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480  60.0*+  59.9
```

---

