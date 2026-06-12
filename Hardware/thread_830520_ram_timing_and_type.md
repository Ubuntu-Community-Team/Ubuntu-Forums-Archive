---
title: "ram timing and type?"
date: 2008-06-15
forum: Hardware
---

### Post by megz on 2008-06-15
hey all,
i recently swapped one of the 512mb ram sticks for a larger 1gig one, and had some questions before i went through and changed it.
[http://ubuntuforums.org/showthread.php?t=830466](http://ubuntuforums.org/showthread.php?t=830466)

i decided to test the new stick and compare it with the old one in memtest (im glad thats included in the grub boot menu :) )

problem is, im now stuck on figuring out which one is better

mentest reads the following for the old sticks (2x 512mb)
RAM 166Mhz DDR 332 CAS 5-5-5-15 / Dual-Channel (interleaved)

on boot the bios shows DDR 667 / CL5

memtest reads the following for the new sticks (1x 512mb 1x 1Gb)
RAM 332Mhz DDR 664 CAS 4-4-4-12 / Dual Channel (asymmetric) 

on boot the bios shows DDR 533 / CL4

any advice / help appreciated :)
thanks

---

### Post by paulisdead on 2008-06-15
Looks like you're mixing different sizes and speeds, which is bad practice.  It also looks like you might be mixing different speed grades of RAM as well, which also isn't a good idea.  The new stuff is lower latency, which is better, but it's slower mhz wise which is bad.  So overall, you're losing dual channel and running at slower mhz, but gaining lower latency, so you're probably losing out on performance there.  If you're starved for RAM, though, with what you do, it still might work better just by having more of it around, even though it's running slower.  

With dual channel setups, you should use all matching dimms, in size mhz, and latencies.  So it's best if you just buy the exact matching model to pair it with.  Frequently systems can run fine with non matching sizes, but in other cases you can get instability.  

With laptops, you don't often have a whole lot of choice, and have to mix and match if some of the RAM is permanently soldered into the system.  If what you're doing really would benefit from more RAM, it's probably worth it.

---

