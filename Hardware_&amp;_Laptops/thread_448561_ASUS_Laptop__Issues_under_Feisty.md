---
title: "ASUS Laptop  Issues under Feisty"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by lord bacon on 2007-05-19
I have an Asus F3Jp laptop that i have installed the fglrx drivers etc. well  anyways i seem to be having a few problems.

first of all i can not get sound to return after i send it to sleep (ie. sound works fine when i first turn it on but once i wake it from sleep it doesnt play any sounds what so ever)
so i would like any ideas on how to fix this.

the second problem is related to CPU frequency scaling, as this is a laptop i would like good battery life, but it seems that cpu frequency scaling is not supported (it is a Core 2 Duo CPU), i have tried a few things and it seems the only way i can get it to "work"(have no way of confirming this) is to put
"sudo modprobe acpi-cpufreq" 
into terminal twice the first time i input the above command it gives a fatal error, the second time it seems to succeed, i tried putting this into 
/etc/modules  
but it still didn't work.
so any ideas on how to fix the above problems would be much appreciated, thanks

---

### Post by simoncullen on 2007-05-20
Yup: put it in twice.

```

simon@frege:~$ more /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
fuse
fglrx
videodev

acpi_cpufreq
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
acpi_cpufreq
simon@frege:~$ 

```

---

