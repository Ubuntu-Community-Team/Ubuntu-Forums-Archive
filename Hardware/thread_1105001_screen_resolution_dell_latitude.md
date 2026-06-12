---
title: "screen resolution dell latitude"
date: 2009-03-24
forum: Hardware
---

### Post by elgr3co on 2009-03-24
I have a dell latitude D610 with a 14 inch screen. I use ubuntu 7.1. My graphics card is ATI Mobility Radeon X300.

I accidentally changed the screen settings from "Screens and Graphics" and now I can't find what the old settings were. Every settings I tried looks really bad.  :(

I have also installed winXP at my laptop and the screen settings there are: resolution 1400x1050, refresh rate 60Hz.

---

### Post by elgr3co on 2009-03-24
ok, consider it fixed. Apparently linux saves the previous configuration files in /etc/X11/ with names xorg.conf.1, xorg.conf.2 etc. so I was able to find the config that worked and revert to it.

---

