---
title: "How intel driver with second high resolution monitor without EDID?"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by udippel on 2009-07-28
Subject says it almost:
I have a notebook with Intel (965), and want to attach a second monitor. Alas, despite of being a high-end monitor (CRT) with 1600x1200, it does not provide EDID info. 
Being on a notebook, I can't disable the built-in screen (1024x768), so the second monitor will always go with the same resolution and same horizontal frequency (60 Hz); in short: lousy and flickery. 
If it was Nvidia, I'd know the Twinview, and DFP settings and whatnot. But how to make that with the intel driver?
I played with /etc/X11/xorg.conf, but to no avail.
I also tried the 'Display' settings (gnome-display-properties), but since it cannot recognize the monitor, it is stuck to 1024x768 at 60 Hz. 
My last effort was xrandr, which shows the same values. I tried to bump them up, as explained in the man page, but it refuses, stating that 1024x1024 is the maximum to set.

Any suggestion welcome,

Uwe

---

