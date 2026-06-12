---
title: "Intel 945GM + i810 + 915resolution = weirdness"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by davidsiegel on 2007-06-27
I have a Lenovo ThinkPad z61t with Intel 945GM integrated graphics and I'm using the i810 xorg driver and trying to use my Dell 2405FPW at its native resolution of 1920x1200. I installed xserver-xorg-video-intel and that got the display working but the laptop would halt when I tried running it with the lid closed and beryl went all white on me. With the i810 driver, I can run the display at 1600x1200 and everything looks a bit fat. I installed 915resolution and overrode a modeline setting for 1920x1200 but I still can't get past 1600x1200. However, in the past week I wrote a script that easily swaps my xorg.conf for switching between the internal laptop display and the external Dell display. Upon testing this, I killed the xserver and/or gdm multiple times in fast succession (either by doing cntrl-alt-delete in gdm maybe four times in a row, or doing /etc/init.d/gdm restart multiple times) and all of a sudden my external display was working at the correct, higher resolution. This behaviour is hard to reproduce and I was wondering if anyone else has experienced similar behaviour with the Intel integrated graphics/915resolution/i810 driver combination.

---

### Post by davidsiegel on 2007-07-02
It looks like if I re/start gdm with my xorg.conf configured to display on the external monitor WITHOUT the external monitor plugged in, THEN plug the external monitor in, I get the optimal 1920x1200 resolution.

---

