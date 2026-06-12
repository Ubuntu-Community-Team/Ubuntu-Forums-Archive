---
title: "P4M Hyperthread procesor scaling freqs under Dapper"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by Rich99 on 2007-06-14
I have a P4M 3.2 hyperthreading processor, and I'm using Dapper drake LTS on it.  I've manually modprobe'd p4-clockmod, and using the basic i386 kernel (2.6.15-28) I can use the cpufreq-selector program to set the scaling governers as required, and they work fine.  However I noticed that on bootup I had an error saying max CPU number reached.  Since I have hyperthreading I switched to the 686-smp kernel.  That gives me 2 cpu's detected, however the cpufreq-selector only works on cpu0.  cpu1 stays on the performance governer.  If I use 'cpufreq-selector -c 1 -g ondemand' there is no error message, but /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor remains as 'performance'.  If I try 'sudo cat ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor' then I get a permission denied error message.

So, at the moment I have cpu0 on 'ondemand' and cpu1 on 'performance' and the scaling_cur_freq files confirm that one is at 800MHz & the other at 3.2GHz (although cpu0 does increase it's speed with workload).

Do I have a problem or not?  I wouldn't have thought that you could have 2 different clockrates with a hyperthreaded processor, since it's not really 2 cores.  Is it just a quirk of linux & hyperthreading that I appear to have this?  Is everything actually OK, and I have ondemand throttling?

---

### Post by CrazyGuy123 on 2007-06-14
I;m not absolutely sure, but since the P4 is actually a single processor  (but emulates 2 processors to be able to do some parallel processing), that means the processor only has a single speed.  I'd say that by setting cpu0 to ondemand, it applies to the actual processor, and the cpu1 scaling is just ignored at some point down the road to the hardware.

EDIT:  just saw the last paragraph of what you wrote - yes, I think it's just a quirk.

---

