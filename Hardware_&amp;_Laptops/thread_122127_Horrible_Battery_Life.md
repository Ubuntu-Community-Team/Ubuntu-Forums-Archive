---
title: "Horrible Battery Life"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by I922sParkCir on 2006-01-26
I have a a Dell Inspiron 700m and the battery life in Windows is 2.5 this was acceptable considering I have an extra battery. In Ubuntu the battery life is a little less than 1.5 hours. In both enviroments I have the sceen brightnes all the was up. Any help would be greatly appreciated. Thank you.

---

### Post by littlewood on 2006-01-26
I get about 4 hours out of mine...

How old are the batteries? were they exposed to cold recently? This can shorten battery life.

If you got 2.5 hours in Windows recently I would check if you have laptop tools installed, check your hdparm options to decrease harddrive load and turn off unnecessary services.
These things might cause increased load on your system and drain the battery.

---

### Post by Game_Ender on 2006-01-26
I have found the kernel doesn't properly detect that it can throttle my CPU down to 200 Mhz of its 1600 Mhz, so it only goes down to 600 Mhz.  I have not been able to manually change the file in /sys/cpu0.  You should fire up the frequency scalling applet and check out the performance.

---

