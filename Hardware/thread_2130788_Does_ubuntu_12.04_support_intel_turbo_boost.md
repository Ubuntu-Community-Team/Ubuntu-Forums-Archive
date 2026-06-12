---
title: "Does ubuntu 12.04 support intel turbo boost?"
date: 2013-03-30
forum: Hardware
---

### Post by swagz101 on 2013-03-30
Does ubuntu 12.04 support intel turbo boost out of the box? If not, how do I enable it?

I have a core i5 3317u

---

### Post by swagz101 on 2013-04-03
Anyone? Is there at least an article where I can read about this?

---

### Post by Doug S on 2013-04-03
Yes it does. As far as I know, enable or disable is typically done via BIOS settings. However, CPU clocking can be controlled via various scaling governor options. There are installable tools to help with frequency scaling options, but I never use them.

To inquire as to current frequencies:```
doug@s15:~/temp$ cat set_cpu_inquire
#! /bin/bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
grep MHz /proc/cpuinfo
doug@s15:~/temp$ ./set_cpu_inquire
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 3401.000   [COLOR=#ff0000]<<< That CPU is in turbo mode, indicated by the "1" at the end[/COLOR]
cpu MHz         : 1600.000
cpu MHz         : 1600.000

```To change governors:```
doug@s15:~/temp$ cat set_cpu_conservative
#! /bin/bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
for file in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo "conservative" > $file; done
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
doug@s15:~/temp$ sudo ./set_cpu_conservative
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
conservative
conservative
conservative
conservative
conservative
conservative
conservative
conservative
```Note that there are issues with some of this stuff, and sometimes incorrect information can be shown for CPU frequencies. The only way to really really know the actual CPU frequencies is to use "turbostat" (not installed by default, and also requires module msr). Example:```
doug@s15:~/temp$ sudo ./turbostat
 cr CPU    %c0  GHz  TSC    %c1    %c3    %c6    %c7  %pc2  %pc3  %pc6  %pc7
          12.51 3.80 3.41  15.30   0.00  72.19   0.00  0.00  0.00  0.00  0.00
   0   0   0.03 3.69 3.41   1.06   0.00  98.92   0.00  0.00  0.00  0.00  0.00
   0   4   0.03 3.67 3.41   1.05   0.00  98.92   0.00  0.00  0.00  0.00  0.00
   1   1   0.04 3.81 3.41  99.96   0.00   0.00   0.00  0.00  0.00  0.00  0.00
   1   5  99.95 3.80 3.41   0.05   0.00   0.00   0.00  0.00  0.00  0.00  0.00  [COLOR=#ff0000]<<< Clock is actually 3.8 GHz.[/COLOR]
   2   2   0.01 3.70 3.41   5.21   0.00  94.78   0.00  0.00  0.00  0.00  0.00
   2   6   0.01 3.58 3.41   5.21   0.00  94.78   0.00  0.00  0.00  0.00  0.00
   3   3   0.00 3.61 3.41   4.94   0.00  95.05   0.00  0.00  0.00  0.00  0.00
   3   7   0.00 3.68 3.41   4.94   0.00  95.05   0.00  0.00  0.00  0.00  0.00
```Hope this helps.

---

### Post by BloodIce on 2013-08-23
The strategy with scripts for the governor works well. Thank you for sharing your idea, Doug! I had a problem with Haswell driving Ubuntu 13.10 (Salamander). Executing the scripts suggested by Doug fixes the problem if you need an extra boost for some application. One option to go back is to create additional set_cpu_ondemand script. Otherwise for a laptop the conservative settings are a battery-killer.

---

