---
title: "CPU Throttling Levels"
date: 2005-12-25
forum: Hardware &amp; Laptops
---

### Post by Sajjen on 2005-12-25
I've got a Acer Aspire 1315LC with a Mobile Athlon XP 2500+ processor. I've got powernowd running and it works nicely. The problem is the levels it's using. The lowest frequency is about 800MHz. When I was using "that other OS" I had a utility called RMClock that allowed me to run the CPU at about half of that at only 0.925V. Battery life is not an issue to me, since the battery is dead anyway, but fan noise and temperature is.

From what I understand the kernel module gets the power states from the BIOS. Is there some way to manually enter the values? Perhaps there is a patch floating around somewhere? Is there some way to see the current core voltage?

Erik

PS. I've already upgraded my BIOS to the newest version and that didn't do anything. DS.

---

### Post by 23meg on 2005-12-25
Do a forum search for undervolting; a guide on it was posted a while ago.

---

### Post by Sajjen on 2005-12-25
It's possible I've missed it, but all I've found is about Centrino based computers.

---

### Post by Sajjen on 2005-12-26
I found a patch at [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml) but I could not get it to work. I've created a patch of my own. It's not pretty, you have to recompile the module to change the throttling levels, but it works.

---

### Post by xyz on 2005-12-26
It may be this you're looking for:
[http://ubuntuforums.org/showthread.php?t=97043&highlight=undervolting](http://ubuntuforums.org/showthread.php?t=97043&highlight=undervolting)
Hope things work out for you!

---

### Post by Sajjen on 2005-12-27
As I said, it's all about Centrino based computers. My own patch works great though...

---

