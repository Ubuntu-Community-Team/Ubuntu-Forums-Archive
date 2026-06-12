---
title: "Dell Latitude D820 Intel Video and Docking station resolution problem"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by ariel on 2007-10-24
My D820 w/Intel video has been upgraded to 7.10 gutsy.

When at the office I use it with a docking station and a viewsonic external lcd monitor, 1440x900.  The laptop has a display with a 1650x1050 resolution.

With Feisty, when booting the machine while docked, I had 1440x900 as resolution. If I booted it while un-docked then I had 1650x1050; life was good with feisty in this front.

With Gutsy, regardless of how the machine is booted, I always get 1650x1050. It seems that the external viewsonic monitor resolution modes are not really seen by gutsy.

displayconfig-gtk proved to be totally useless in this case, it can't even detect the laptop's internal display resolution modes, and for the second display (the external viewsonic) it offers 640x480 max.

Running xrandr with both displays connected (and being (badly) cloned)  displays only the resolution modes of the laptop's own display. The external monitor 1440x900 does not show up anywhere. 

I tried adding 1440x900 in the Display subsection in xorg.conf, no luck, still not showing up. 

I wouldn't mind too much rebooting the laptop each time I change from internal to external monitor, as long as the resolutions are OK.

Any hints or suggestions?? Thanks!

---

### Post by ariel on 2007-10-25
Found the problem: the Gutsy upgrade left the machine using the i810 driver instead of the intel driver, in xorg.conf.

Changing the driver enabled xrandr to see both the internal lcd and the external monitor, docked or undocked. And the right resolution showed up in each of them without having to use xrandr or displayconfig-gtk.

Additionally, the machine can now do suspend with no problems.

---

