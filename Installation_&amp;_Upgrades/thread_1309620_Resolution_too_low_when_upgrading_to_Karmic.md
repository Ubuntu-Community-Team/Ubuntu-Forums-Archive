---
title: "Resolution too low when upgrading to Karmic"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Siggij on 2009-11-01
My graphics card:
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

Runs the i915 intel graphics driver and the maximum resolution is 800x600 which is way to low for my needs. Anybody have a fix for this issue? Going back to a former kernel gives me higher resolution but then in a few minutes the screen goes blank and there's nothing I can do.

Had to revert to Jaunty to get proper resolution.

---

### Post by craig.o on 2009-11-01
> **Siggij said:**
> My graphics card:
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

What worked for me in the past when I had a situation like this (i810/i830 systems in ubuntu 8.10) was to either copy the xorg.conf file over from the old (working) system or generate a new xorg.conf file (man Xorg -config) and editing the file.

hth,
-Craig

---

### Post by Siggij on 2009-11-01
Thanks but when I looked for it in Karmic there wasnt a xorg.conf file. Maybe it would have worked to generate a new one. There is one in Jaunty so Ill try to copy it over. Thanks again.

---

### Post by some1_genius on 2009-11-10
Hay! buddy, This old driver worked for me in Ubuntu 9.10, try it.
[https://launchpad.net/~siretart/+archive/ppa/+sourcepub/567922/+listing-archive-extra](https://launchpad.net/~siretart/+archive/ppa/+sourcepub/567922/+listing-archive-extra)
its xserver-xorg-video-intel-2.4  2:2.4.1-1ubuntu11. While the current driver is xserver-xorg-video-intel 2:2.9.0-1ubuntu2.
hope it works for u.

---

### Post by some1_genius on 2009-11-10
unfotunately, compiz doesn't work with this old driver.

---

