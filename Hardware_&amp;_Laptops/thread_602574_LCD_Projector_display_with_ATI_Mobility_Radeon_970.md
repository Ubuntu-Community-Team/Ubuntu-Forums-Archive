---
title: "LCD Projector display with ATI Mobility Radeon 9700"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by obiwankamote on 2007-11-04
Hi guys. I've been having problems setting up the connection to an external LCD projector since the pre-release of Gutsy Gibbon, but still have some problems. Here are the details of my system.

Acer Aspire 1680wlmi
ATI Mobility Radeon9700
-used XGL
-used the open source ati drivers (fglrx)

At first, when I connected the projector during boot up, it shows on the projector up to the ubuntu loading screen but reverts to low graphics mode when it detects the projector.

Eventually, from a forum I got to show the graphics on the projector by doing the following:

In the shell:
$ export DISPLAY=:0

$ aticonfig --enable-monitor=crt1

This got the connection working. I could return it to the LCD by using 

$ aticonfig --enable-monitor=lvds

The problem is, this only displays the screen either on the LCD projector or on my laptop screen. I want to display it on both. Using this ..

$ aticonfig --enable-monitor=crt1,lvds

Causes the display to crash. It then goes back to the login screen.

Any ideas on how to go about this? Also, from the forum, it said that i had to change the display to 0 (export DISPLAY=:0) because of XGL. Anyone who can explain it a bit further? Would this probably affect my problem with the LCD projector output?

Thanks!

---

### Post by obiwankamote on 2007-11-08
No one encountered this same issue?

---

