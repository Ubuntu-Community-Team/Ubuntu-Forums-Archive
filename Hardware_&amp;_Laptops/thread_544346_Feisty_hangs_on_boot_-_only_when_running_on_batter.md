---
title: "Feisty hangs on boot - only when running on battery due to wireless / ndiswrapper"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by Cybergy on 2007-09-06
This issue is more of a pain-in-the-butt than anything else right now, but it seems to me that it should be quite solvable.  I have yet to find a solution that applies to my config.

I am running Feisty 7.04 on a Dell D505 (with a Dell Trumobile 1400 wireless card) and ndiswrapper 1.47.  When I boot with A/C plugged in, the system boots fine - and works great (Feisty rocks!).  However, if I boot running on battery power, the system hangs on boot.  I can boot using A/C and unplug afterward with no problem running on battery.  My searches indicate the issue relates to ndiswrapper or hotplug subsystem - but I still have not found the magic bullet to fix the problem.

I'm not a linux guru but I take instruction well ;-) 


I've seen many posts on this issue, but no real solutions.  One solution is to disable wireless in bios before booting up - but that's pretty lame.  Another solution recommended editing /etc/init.d/hotplug - but that file doesn't exist on my system.

Does anyone know how I can get rid of this issue?

---

### Post by kgr132 on 2007-10-07
Me too. Dell Latitude D600 running Feisty. Same exact symptoms as described above. Help?

---

### Post by StevoG7 on 2007-12-08
The symptoms are the same with my D600 machine running Gutsy, so far I have not found a fix.

---

### Post by StevoG7 on 2007-12-09
Hey I've found a fix for this on my machine.  When turning on the computer enter the bios setup screen (f2).  Find the quick boot bios option and disable it, or if it is set to minimal boot set it to thorough.  It takes a few more seconds to load the bios and boot but nothing thats a problem.  Try it out, it worked for me, good luck.

---

