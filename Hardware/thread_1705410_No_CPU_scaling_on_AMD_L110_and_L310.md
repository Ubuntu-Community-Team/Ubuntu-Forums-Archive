---
title: "No CPU scaling on AMD L110 and L310"
date: 2011-03-12
forum: Hardware
---

### Post by fenofonts on 2011-03-12
Hi All, my laptop configuration is:
Packard Bell Dot M/A (This model is pretty much the same as the Gateway LT3100)
AMD L110 1.2GHz upgraded to L310
ATI X1270 GPU
2GB RAM
64GB Crucial C300 SSD drive


On Ubuntu 10.10 I notice the fan is on all the time and there seems to be no solution for scaling or undervolting the CPU. This has been the case with both the L110 and L310 CPUs.

My problem is that when I upgraded to the dual-core AMD L310 CPU, even though the CPU is the same 13W (maximum) as the L110, the system is taking a little more power and as a result the laptop can barely charge when the laptop is turned on. Typically, the 6-cell battery would take about 3 hours to charge, but since the upgrade it takes about 10 hours when laptop is on.

So I either need to undervolt my CPU somehow, or to try a power supply with about 5W more than my current 30W one.

Any suggestions anyone?

---

### Post by fenofonts on 2011-03-13
Hi again, I have seen that Liteon does a power adapter of 2.1A/19V rather than the original 1.58A/19V effectively giving 40W instead of 30W. 

I don't know at this moment if the extra 10W would fry my laptop, but I do know for sure that without undervolting/scaling the CPU my battery will not last as long, so I will only try the bigger power supply as last resort.

---

### Post by fenofonts on 2011-03-15
Solution found!!! thanks to Cubicsilver on page 6 of this thread:
[http://ubuntuforums.org/showthread.php?t=1471701&page=6](http://ubuntuforums.org/showthread.php?t=1471701&page=6)

There is a custom BIOS which allows all the MB tweaking I needed to enable scaling!!!

---

