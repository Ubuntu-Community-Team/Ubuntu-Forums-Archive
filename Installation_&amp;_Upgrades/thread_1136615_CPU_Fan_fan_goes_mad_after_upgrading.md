---
title: "CPU Fan fan goes mad after upgrading"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by biglog on 2009-04-25
Have recently upgraded to 9.04 from 8.04 via 8.1.

In both 8.1 and 9.04 CPU fan has gone mad.

It used to run at around 2400-2800 RPM in 8.04.

It now runs at about 4200-4500 RPM non stop.

I have done a bit of web searching and think it may be something to do with frequency-scaling.  Runs at around 4500 RPM at rest in "performance mode"  and around 4200 RPM in "power save mode"


This is really annoying since my fan is quite loud at 4000 RPM.

Can some one point me in the right direction.


Log

---

### Post by biglog on 2009-04-26
Will this work for Jaunty? - It is an old thread

[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

---

### Post by Triptol on 2009-04-26
Can't guarantee, but that looks like it might work.

---

### Post by biglog on 2009-04-28
modified /etc/fancontrol

increased MINTEMP & MAXTEMP - runs at about 2800 rpm at rest now which is OK

---

