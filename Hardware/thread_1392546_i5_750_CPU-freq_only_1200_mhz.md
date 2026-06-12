---
title: "i5 750 CPU-freq only 1200 mhz"
date: 2010-01-28
forum: Hardware
---

### Post by sunfire on 2010-01-28
Hi,

my problem is that my new i5 750 cpu and all it's 4cores are showed only as 1200 Mhz all the time. They should be 2,76Ghz atleast on on somepoint. Even when  build the package all cores stay at 1200mhz.

I tried this but _no help:_

1. Installed rcconf. (In terminal sudo apt-get install rcconf).
2. Opened it with terminal. (sudo rcconf)
3. Found "On Demand" service and disable it. 
4. Rebooted PC and all cores are changed to performance mode.

-------------------------------------------------------
CPU: i5 750
Motherboard: Asus P7P55D-E 
Kernel: 2.6.31-17-generic x86_64
-------------------------------------------------------

Anyone else having same type of problem ? is this kernel problem or should i turn some BIOS features off ?





EDIT:
Founded way to put cpu-freq to "normal" all the time. -> [http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)

sudo -s
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor

4times to make all cores to use "normal" cpu-freq. Not sure if this is right way to do this, but it's looks working atm.

---

