---
title: "xorg.conf doesn't work in 11.10"
date: 2011-11-07
forum: Hardware
---

### Post by oversky on 2011-11-07
I have a xorg.conf that works in Ubuntu 9.10.
The xorg.conf adds a new modeline and setup dual monitors.
Recently, I tried Xubuntu 11.10, and sadly found that the same xorg.conf doesn't work anymore.
To be more precisely, I did see the wallpaper showed in the correct resolution in the beginning, but then my first monitor, Dell 2007FP, turned black.
I checked with xrandr -q, and found that the new modeline doesn't exist.
I also tested the same xorg.conf in debian 6.03, no problem at all.
My guest is that the new Xubuntu  adds some kind of screen auto detection, 
and this cleasr the setting in xorg.conf, and .xprofile.
Is it possible to turn off the auto detection process?

My system is IBM T42 with ATI RV250 chipset.
The Dell 2007FP has a native resolution 1600x1200.

---

### Post by xavi on 2011-11-14
I have no idea why this happened, but I found a quick workaround:

sudo apt-get install grandr

and select there the desired display of monitors by means of "Menu > System > Multiple Screens". Choose. Apply. Save. Done

I hope it helps, in the meantime they find a proper fix to this issue.

Cheers

---

