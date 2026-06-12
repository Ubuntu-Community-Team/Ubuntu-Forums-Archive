---
title: "How to check the actual cpu clock speed?"
date: 2010-08-08
forum: Hardware
---

### Post by shuffman37 on 2010-08-08
I've used 

-sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
-sudo cat /proc/cpuinfo

Along with many other apps. 

They all say my CPU is running at 2900mhz. Athlon ii x2 245 which is correct. The frequency scaling app on gnome panel says the same, and individual core clocking works. Why when I overclock my CPU to say 3055mhz, it doesn't detect it within the OS and still says 2900mhz?

---

