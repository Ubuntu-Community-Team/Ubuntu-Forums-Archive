---
title: "External monitor problem"
date: 2009-08-08
forum: Hardware
---

### Post by Blue1 on 2009-08-08
My setup:
Ubuntu 9.04
IBM Thinkpad T60p
Ati Radeon Fire GL V5200 256mb graph.
Ibm Mini-dock
Monitor HP LP2475w
No additonal drivers installed

Connected via DVI from my mini-dock I can't get my external monitor to work correct.

In Gnome System / Display there is no option to select 1920x1200 resolution. xrandr shows it's perfectly connected and has 1920x1200 as an option.

xrandr --output DVI-0 --mode 1920x1200 take care of the problem not being able to select the proper resolution in gnome but it does not work satisfying.

Now, when in full res mode, there are disturbances in the display. The area around the mouse pointer sort of flicker(maby it's around all moving objects). Seems to get worse when having multiple windows open. Also the whole screen flicker sporadic.

Does anyone know how to tackle this problem? There is nothing wrong with the monitor.

---

### Post by Dave_Connor on 2009-08-08
Sometimes laptop have issues with high-res video, have you tried your external on a lower resolution ?

---

### Post by Blue1 on 2009-08-09
> **Dave_Connor said:**
> Sometimes laptop have issues with high-res video, have you tried your external on a lower resolution ?

Yes I've tried lower res. The screen seems to work on these lower res.

However, it's not possible that this is a laptop issue. I've used the same combination in win xp for months with excellent results.

Must be an Ubuntu, ATI or Gnome issue.

---

### Post by Dave_Connor on 2009-08-09
Have you tried a another driver ?
If you are using ati driver then try the radeon driver on your system in your /etc/X11/xorg.conf.

---

