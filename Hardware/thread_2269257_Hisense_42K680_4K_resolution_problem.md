---
title: "Hisense 42K680 4K resolution problem"
date: 2015-03-14
forum: Hardware
---

### Post by blazeag on 2015-03-14
Hi everybody, I just bought a Hisense 42" 4K monitor and connected it to my Ubuntu 14.10 PC. Strangely it is recognized as a generic Hitachi 52" (yes, 10 inch more) and max resolution is 1920x1080.
I have a GeForce 8600GT with two DVI output. I use a DVI -> HDMI adapter to connect to HDMI port. I use nVidia binary drivers 340.76 (open source).

I manually added 3840x2160 in /usr/share/X11/xorg.conf.d/10-monitor.conf and now max monitor resolution is listed correctly, but if I choose it, a blank monitor is all what I get.

[Edit]
Problem was simpler than it could seem: GeForce 8600 can't handle resolutions more than 2560x1600.

---

