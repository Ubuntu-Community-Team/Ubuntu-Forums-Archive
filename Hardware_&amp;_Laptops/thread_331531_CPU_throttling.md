---
title: "CPU throttling"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by lcaley on 2007-01-04
Hey everyone, first off, I'm not sure if this should be in the hardware or software forum, so if this is the wrong forum, i apologize. I've been through a huge ordeal to get my second cpu working. But it is finally working. The only thing I have left that I want to do, is when I reboot, the cpus default to the 'ondemand' governor and I want it to set to the 'conservative' governor. If I change it manually for each cpu with the 'sudo cpufreq-set -c <cpu number> -g conservative' command, the cpus do exactly what they're supposed to until I reboot. I assume that I'll have to write some kind of script to do those commands when I log in, but I don't know how to do that, or where to put it.

I'm fairly new to linux, but I do know a little bit, so please keep that in mind with your responses.

Thanks!

---

