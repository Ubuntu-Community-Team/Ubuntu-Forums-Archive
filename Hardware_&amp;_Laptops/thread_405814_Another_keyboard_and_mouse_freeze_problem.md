---
title: "Another keyboard and mouse freeze problem"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by brm on 2007-04-10
KDE is frequently largely unresponsive after a period of inactivity. I do not yet know if this problem is unique to KDE or if it affects other environments equally. The period of inactivity is sometimes as short as three or four minutes, that is, somewhat before the screensaver is set to start, which is five minutes. A screensaver password is set to be activated after 900 sec (15 minutes) (aside: although it is a longstanding annoyance that the password is always required long before the 15 minutes have run out).

This problem plagues Etchy and all development releases (so far) of Feisty. I did not experience it in Breezy or Dapper.

I doubt that the problem arises from defective hardware. I have tried different keyboards and mice, all of which I know to work normally. All devices have built-in PS/2 connectors; none use USB-to-PS2 "adapters".

The detailed symptom is a "substantial unresponsiveness" rather than a hard freeze. The mouse moves about the screen, raises and lowers the panel and hovering brings up "balloons". But clicks are never processed. With the keyboard, Clt-Alt-Fx works to bring up login consoles. Ctl-Alt-Bksp allows works, allowing a brute force restart of X. No other keystrokes are processed.

Sometimes, but not often, switching to a login console, working there for a minute or so and returning to X restores responiveness to the graphical session.

A check of system resources shows that X.org, all KDE components and Firefox are all consuming limited resources (<5% each), often less.

The video card is based on the nVidia FX5700 chipset with 256MB RAM. The problem arises with both the "nvidia" and "nv" video drivers in Xorg (although, admittedly, I use the proprietary driver >95% of the time).

Is this problem known to the Ubuntu developers? I have looked carefully (at least, I thought it was carefully :-) ) but have not succeeded in finding a bug report which covers these symptoms. But the same has also been true of many other problems which I have reported, only to find that mine was a duplicate of an existing bug.

---

### Post by dan171717 on 2007-04-11
its probblely an undocumented bug in kde ive never used it but ive herd gnome is more reliable???

---

