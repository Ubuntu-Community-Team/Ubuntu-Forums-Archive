---
title: "CPU frequency scaling 85% - 100%, good or bad?"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by nixi on 2008-02-03
Hello!

I use a pair of Intel Xeon E5345 quad core CPUs on a Tyan i5400XT board, and according to Ubuntu's Ondemand sensor panels their cores run at 85% minimum load for idle and ordinary tasks. 

Another computer with an AMD Athlon 5600+ runs at 35% minimum for idle or ordinary tasks according to Ondemand. That seems a lot more reasonable.  

It occurs to me 85% is far too high for a minimum.Yet I can't find a "speed stepping" setting, or the like, in the motherboard's BIOS, and since I don't know where to look for more information I post here. 

Do you know if this has to do with a difference between AMD and Intel CPUs in general, or is it more likely a motherboard thing, or a software incompatibility thing?  Suggestions?

---

### Post by Yellow Pasque on 2008-02-03
It has to do with the difference between Intel and AMD's underclocking methods.

The E5345 uses a system clock of 333MHz and has a multiplier of 7 for a stock speed of 2.33GHz. Intel's Speedstep technology reduces the multiplier to 6 at idle. This works great on chips with lower system clocks (like Core Duo's or mobile C2D's), but as you see, it doesn't make much of a difference on your CPU (6 *333 = 2GHz).

AMD doesn't use a FSB like Intel, so they work fine with a lower base clock (200MHz), and the multiplier goes down to 5 (1GHz) at idle, along with a drop in core voltage to 1.1V

That's the why of it, but I don't know what to suggest as I'm not familiar with using custom underclocking/volting on Intel's side. I know for AMD, the powernow-k8 file can be recompiled and built into the kernel if you want to select your own voltage/clocks, but I don't know about Intel. Sorry.

---

### Post by nixi on 2008-02-04
Thank you! Your reply is very informative. It seems then this is the way these CPUs work...

I bought them with Intels passive heat sinks, which seem to get rather hot (core temperature tends to reach 79°C on 100% load). So I might replace them with a pair of Noctua coolers.


EDIT
The Noctua coolers, or their Xeon mounting kit, won't fit this motherboard, so I bought a pair of Verax X21 NGA instead.

---

