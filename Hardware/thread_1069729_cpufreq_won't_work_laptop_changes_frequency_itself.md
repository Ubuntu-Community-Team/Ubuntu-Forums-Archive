---
title: "cpufreq won't work? laptop changes frequency itself randomly"
date: 2009-02-14
forum: Hardware
---

### Post by vajorie on 2009-02-14
I don't understand why, but I cannot control frequency with cpufreq. The laptop will just use whatever frequency (either 2.10 or 2.80) it wants regardless of what I say. And there seems no reason why it's changing frequency. 

One problem that seems obvious is a failed modprobe for acpi_cpufreq on boot:
it says "could not load module, device or resource busy"

I tried to unload cpufreq_stats (to load acpi_cpufreq first and then cpufreq_stats, but it gave me a segmentation fault). 

This is a HP Pavilion zv5120us laptop with a BIOS updated to F.45

The reason I am trying to play around with this is that the laptop was sluggish and I found that it was running at freq 2.10 a lot... Wasn't a problem in Dapper. All I want is for it to set freq an 2.80 and neither cpufreq-set (I did the chmod +s thingy) nor sudo cpufreq-set nor the cpufreq-applet will do it. 

my cpuinfo: 
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Celeron(R) CPU 2.80GHz
stepping	: 9
cpu MHz		: 2800.000
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
bogomips	: 5604.10
clflush size	: 64

```

cpufreq-info (when freq is 2.80):
```

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 350 MHz - 2.80 GHz
  available frequency steps: 350 MHz, 700 MHz, 1.05 GHz, 1.40 GHz, 1.75 GHz, 2.10 GHz, 2.45 GHz, 2.80 GHz
  available cpufreq governors: powersave, conservative, userspace, ondemand, performance
  current policy: frequency should be within 2.80 GHz and 2.80 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.80 GHz.

```

cpufreq-info (when freq is 2.10 - I can't change it myself)
```

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 350 MHz - 2.80 GHz
  available frequency steps: 350 MHz, 700 MHz, 1.05 GHz, 1.40 GHz, 1.75 GHz, 2.10 GHz, 2.45 GHz, 2.80 GHz
  available cpufreq governors: powersave, conservative, userspace, ondemand, performance
  current policy: frequency should be within 2.10 GHz and 2.10 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.10 GHz.

```

my sysfs.conf (I just need the full power - my battery is ded, so this is like a desktop)
```

devices/system/cpu/cpu0/cpufreq/scaling_governor = userspace
devices/system/cpu/cpu0/cpufreq/scaling_setspeed = 2800000

```

/etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
p4-clockmod
cpufreq_ondemand
cpufreq_userspace

```

pls let me knos if more info is needed.

---

### Post by vajorie on 2009-02-14
bump 

also, I tried monitoring the freq & temp, and it seems like the frequency is slowed down when the temperature is increasing *fast*, and comes back to normal when the temp starts decreasing, with a treshold of about 55 degrees. on the other hand, sometimes when the temp stays around even 56 degrees or more, it won't decrease the frequency. I've got no idea what's doing it (powernowd is uninstalled). here's the code I used, if anyone else needs it

```

while true; do sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq; cat /proc/acpi/thermal_zone/THRM/{temperature,state}; sleep 2s; done

```

---

### Post by vajorie on 2009-02-15
the random change was due to high and increasing temperature. I cleaned the heat sink (decreasing average heat by about 10-15 degrees celcius) and it no longer steps down the freq. 

I still cannot change the freqs myself though -don't know why.

---

