---
title: "Can't Boot Ubuntu W/out AC Power"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by HieroPosche on 2007-09-01
So I'm dual booting XP and feisty on my laptop (for WoW purposes only I assure you) and for some reason when I try to boot without the AC power plugged in Ubuntu hangs up about 1/4 through the loading bar at startup.  If I select XP, or sometimes even another kernel version, it loads up fine.  Starting up with the power plugged in never had a problem. Any ideas?

---

### Post by HieroPosche on 2007-09-04
Should I feel accomplished that I stumped everyone? :P

---

### Post by phocis850 on 2007-09-04
I don't believe you gave enough information.  What type of laptop, ram, hd, video card...

But, it obviously is a kernel issue with your computer.
Just use the kernel that works and send in a bug for the kernel that doesn't.

---

### Post by coffecup1978 on 2007-09-04
Hi,
I'm actually experiencing the same problem, the laptop boot ok with the power cord plugged in, however, it does halt after three "bars" during boot without. This is on a Dell latitude D600. I will go back in the logs to see if I can see a reason.

Cheers!

---

### Post by StevoG7 on 2007-12-08
Same problem running Gutsy on a Latitude D600
30 gb hard drive, 1 gb ram, ATI radeon mobility 9000 graphics card

---

### Post by StevoG7 on 2007-12-09
Hey I've found a fix for this on my machine.  When turning on the computer enter the bios setup screen (f2).  Find the quick boot bios option and disable it, or if it is set to minimal boot set it to thorough.  It takes a few more seconds to load the bios and boot but nothing thats a problem.  Try it out, it worked for me, good luck.

---

