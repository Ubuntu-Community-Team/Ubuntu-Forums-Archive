---
title: "Laptop reads charging while discharging, i7 CPU problems."
date: 2012-05-29
forum: Hardware
---

### Post by aeqel on 2012-05-29
Hello,

I have a Lenovo Ideapad Y560p, i7 Q2630QM, 8GB RAM, Fresh install Ubuntu 12.04 LTS (64-bit), Kernel Linux 3.2.0-24-generic, Running Classic Gnome.

** Problem 1 [UNSOLVED]: Battery reads charging when discharging.**
I have a SANYO L09S6D16 Battery according to my power statistics in Ubuntu. 

The battery charges fine with the AC Adapter plugged. However, when I unplug the AC adapter instead of reading "discharging" the system reads the battery as "charging" while if I look at the statistics of the charge graph the gradient of the graph is definitely negative.
**Consequence: It's impossible to get an ETA till dead and very hard to know the amount of charge of the battery. **



** Problem 2 [UNSOLVED]: i7 Q2630QM, not throttling, one core/thread always at 100% load.**
This is somewhat self explanatory and obviously has very bad consequences for a laptop and the life/performance of the machine. 
[B]Consequence: I have been forced to set the CPU frequency to 800MHz using the CPU Frequency applet in order to stop overheating as it doesn't throttle down when set to On-Demand. 


[/B]
** Problem 3 [SOLVED]: Intel WiFi card stopped working after doing a dist-upgrade from a fresh install.**
This I am just mentioning for other people who may have the same issue of me; I was able to solve this problem by following the answer here:
[http://askubuntu.com/questions/130499/how-do-i-fix-slow-wireless-on-intel-wireless-cards](http://askubuntu.com/questions/130499/how-do-i-fix-slow-wireless-on-intel-wireless-cards)

Thanks,
):P

---

### Post by aeqel on 2012-06-03
bump

---

### Post by aeqel on 2012-06-04
> **aeqel said:**
> bump

bump

---

