---
title: "Opteron 185 cpuinfo?"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by Roland of Gilead on 2007-12-30
On Santa's recommendation, my wife purchased an AMD Opteron 185 CPU for me for Christmas.  A little birdie mentioned that it's the fastest CPU ever produced for the Socket 939 platform that I'm using.

So, I've swapped it in place of my old Athlon64 3700+, and am now enjoying the dual-core goodness.

Interestingly enough, when I cat /proc/cpuinfo, it shows both cores running @ 1.0 GHz.  Needless to say, this CPU is clocked @ 2.6 GHz, so I'm a bit puzzled.

Anyone have any idea what's going on here?  I can't seem to find a whole lot of CPU benchmarking tools for Linux.

---

### Post by fixture on 2007-12-30
your cpu is probably runnung on power management, look up /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor, if you are running on conservative, ondemand, or powersave, then your cpu is running just fine, when you actually need to calcualte something the freq will be bumped back up

---

