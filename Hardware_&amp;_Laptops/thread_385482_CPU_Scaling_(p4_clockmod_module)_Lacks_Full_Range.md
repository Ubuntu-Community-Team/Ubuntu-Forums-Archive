---
title: "CPU Scaling (p4_clockmod module) Lacks Full Range"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by rjray on 2007-03-15
I recently had to re-install Dapper after an attempted upgrade to Edgy failed horribly and left my system barely usable. I have a HP Pavilion zd7000, and I use kernels that have Software Suspend2 built in to them (using an alternate repo). I tweaked things to make sure that CPU scaling was enabled, but prior to the re-install my CPU would go down as low as 1.45GHz or so (the chip is rated at 2.8GHz). Now, it only goes as low as 2.10GHz, which means it runs hotter and the (annoyingly-loud) fan runs more than it used to.

I've checked the file "/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies", and confirmed that it only lists three steps (2.10G, 2.45G and 2.80G). How do I get back to the full range? Unless I'm speeding along in Eclipse or running a "make" of some source tree, I don't need the CPU running this hot.

Randy

---

### Post by dangermouse28 on 2007-05-21
Your problem is that you're running dapper.

Can't remember exactly what it was, but there's a limitation associated with the p4_clockmod module in dapper which limits the min frequency to 2.1GHz.

I've installed Feisty on my zd7000 and the limitation is no longer there - now min freq is 375MHz  :D

Actually, it's too low - I get scrolling delays etc until the cpu speeds up. I'll try editing the cpufreqd conf file to set the min frequency to 750MHz to sort it out.

---

