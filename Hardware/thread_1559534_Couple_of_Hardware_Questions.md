---
title: "Couple of Hardware Questions"
date: 2010-08-23
forum: Hardware
---

### Post by FireDemonSiC on 2010-08-23
Hey guys.

I see that Ubuntu has been throttling my CPU to half speed (1300mhz).  I can disable this with a command I found but it doesn't permanately turn it off.  The system can still throttle back to 1300mhz.  How do I permanately disable CPu throttling?

Also, I see that Ubuntu is only recognizing around 3.8GB of RAM when I have a total of 4096MB.  My system BIOS first had this problem until I manually set the SPD settings and voltages.  The BIOS recognizes the full 4096 as does windows 7, but Ubuntu does not.  What could be causing this error?

---

### Post by cascade9 on 2010-08-23
I *think* if you remove the "cpufreqd" and "cpufrequtils" packages then your CPU should run at ful sped at the time. I dont know for sure, as I've never tried removing it. Its good for power and heat reduction, and if your computer is under any load, it ramps back up to full speed. 

As for the 3.8GB/4GB issue, ubuntu is probably reporting you real amount of RAM avaible to your system (windows can lie about this). Though it is possible that you dont have the PAE kernel running, limiting you to 3.something BG of RAM.

---

