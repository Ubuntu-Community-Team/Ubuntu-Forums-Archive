---
title: "Thinkpad x200t x200 tablet finger touch multitouch calibration woes"
date: 2013-09-02
forum: Hardware
---

### Post by wrkr1 on 2013-09-02
Hello everyone! 

I have an Ubuntu 13.04 running on a Thinkpad x200 tablet.

Stilus works a-OK, but finget touch does not work well: it acts very weird and almost completely drops off at the edges.

I have read multitudes of posts on how to get the touch input calibrated, but between my older writeups (that seem to be incompatible with never versions of Ubuntu) and my lack of working knowledge of Linux I have had troubles getting things to work correctly.

I have already messed up the instalation 3 or 4 times this week to a point where I had to reinstall. I have exact same issues with 12.04.

I figured I should just make a fresh install and ask for your guys' guidance on the matter as to stop stumbling in the dark.

Thanks a lot!

:)

---

### Post by wrkr1 on 2013-09-02
Favux  ( [http://ubuntuforums.org/member.php?u=699990](http://ubuntuforums.org/member.php?u=699990) ) If you are still around, please chime in!

---

### Post by Favux on 2013-09-04
Hi wrkr1,

Hopefully it is just a question of calibrating touch.  Touch had to be calibrated for earlier tablet PC touchscreens.  The coordinates for the Thinkpad X200t's are available in the tablet PC scripts in post #2 at:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

They are:
```
xsetwacom set "Serial Wacom Tablet touch" topx "48"
xsetwacom set "Serial Wacom Tablet touch" topy "90"
xsetwacom set "Serial Wacom Tablet touch" bottomx "915"
xsetwacom set "Serial Wacom Tablet touch" bottomy "940"
```
Of course the commands were consolidated in the meantime for xsetwacom and it would now be:
```
xsetwacom set "Serial Wacom Tablet touch" Area 48 90 915 940
```
See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration)  You'd still use topX and bottomY etc. Options for xorg.conf.d or xorg.conf.

Good luck.

---

