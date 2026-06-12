---
title: "Dual Core hibernation &amp; Suspend weirdness"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by Foxen on 2006-10-20
Allright, after some fiddling I've gotten quite accustomed to running linux, I even ditched M$ "PlayGround" XP to have a greater incentive in getting things going the way I wanted... There is just one thing that's bugging the heck outta me now, hibernate and suspend works flawlessly except for one thing. This is a Turion X2 laptop, dual core, everything works perfect until I hibernate or suspend, when it comes back out of hibernation/suspend the second core is constantly running 1.6GHz while core 0 still scales with load. What could possibly make this happen? I've tried to uninstall the guidance-power-thing that's installed and tried out both klaptopdaemon and kpowersave but it still exhibits the same thing, any bright ideas?

No matter if it'll ever work I think I've found home now, M$ is way too intrusive to use anymore and gaming, well, get yourself a couple of kids and you'll run out of time to play games ;)

---

### Post by daniel2501 on 2006-10-21
Just to add me in. I had the same problem with my Intel based Core Duo laptop. Suspend and hibernate result in a locks system. Haven't checked the err logs yet though.
-D

---

### Post by benhall on 2006-10-21
I've been having a related problem

[http://www.ubuntuforums.org/showthread.php?t=280862]("http://www.ubuntuforums.org/showthread.php?t=280862")

If true, it might be a kernel bug. Its preventing me from hibernating though, and I think it might be related to a problem where hibernation corrupts my swap.

---

