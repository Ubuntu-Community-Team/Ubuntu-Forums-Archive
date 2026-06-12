---
title: "Elographics driver in repository contains crash bug"
date: 2013-01-09
forum: Hardware
---

### Post by subi211 on 2013-01-09
I've hooked up a serial Elo touchscreen to my PC, and after some fiddling got X to notice it.  However, as soon as the screen is touched, X crashes out.

This bug was found in xserver-xorg-input-elographics/1:1.3.0-1 and fixed in xserver-xorg-input-elographics/1:1.4.1-1 ([Debian bug report here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=688207")).  However, the version in the Ubuntu repositories is still 1:1.3.0-1build2 and still contains the crash.

When will the fixed version be added to the repositories?

EDIT: Ignore the "Ubuntu 10.04 Lucid Lynx" in the user info to the left, I'm using 12.04.  But I can't change it because I'm not a regular here.  :)

---

