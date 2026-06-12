---
title: "Memory upgrade brought my system to it's knees!"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by sitara on 2006-02-02
I have been running Kubuntu (Breezy) quite happily with 512MB RAM for several months. Yesterday I installed Sun Java Studio Creator 2, which has a pre-req of 1GB RAM. It was running a bit slowly, so I went out and bought the extra DIMM (DDR400). The system wouldn't boot. It got as far as 'Loading Modules' on the splash screen then just hung (or that's what I thought). I booted in recovery mode and the system did eventually boot, but it took forever (like 20mins+).

I got a different brand of memory. Same problem. If I put either DIMM in either slot on it's own, it would boot as usual, but as soon as I put both in at the same time... meltdown. 

I was not able to find another DIMM of the same brand as my original one (King max), so I bought two new ones on a 'sale or return' basis. Still sloooow. 

I ran memtest86 from the Ubuntu boot menu on both DIMMS - clean. 

I have noticed a couple of strange symtoms (maybe). Some of the memory tests slow down when they reach the top 50MB addresses. I also noticed that the hardware memory test rattles through the first 950MB of memory and then slows down considerably for the last 50MB. This suggests that the problem is not with Ubuntu, so I may be posting in the wrong place, but I would really appreciate any suggestions. I've got some urgent Java development to do and Sun's Creator looks like the right tool fo the job!

---

### Post by coolclassic on 2006-02-02
Have a look at this:
[http://www-math.cudenver.edu/~jmandel/mri/super-6010-thread.htm](http://www-math.cudenver.edu/~jmandel/mri/super-6010-thread.htm)

It covers areas like dropping the ram speed, recompiling you kernel and and bios configuration.

Hope it helps

---

### Post by sitara on 2006-02-09
I reset my BIOS to optimised defaults and lo and behold....

---

