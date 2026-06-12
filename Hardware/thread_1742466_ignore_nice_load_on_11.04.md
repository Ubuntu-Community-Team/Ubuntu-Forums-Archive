---
title: "ignore nice load on 11.04"
date: 2011-04-28
forum: Hardware
---

### Post by dasy2k1 on 2011-04-28
I would like to make my cpu throttling ignore nice loads so that boinc dosent keep my cpu running at max speed


on 10.10 (maverick) and before i simply set the value of /sys/devices/cpu/cpufreq/ondemand/ignore_nice_load to 1
however this dosent seem to exist in 11.04 (natty) 

any ideas to where it has been moved to?

---

### Post by dasy2k1 on 2011-04-28
meh, found it, 

its in /sys/devices/**system**/cpu......

---

