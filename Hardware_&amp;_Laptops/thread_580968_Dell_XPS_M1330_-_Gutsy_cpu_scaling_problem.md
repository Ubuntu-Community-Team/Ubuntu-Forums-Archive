---
title: "Dell XPS M1330 - Gutsy cpu scaling problem"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by Oxymeron on 2007-10-19
Hi!

Yesterday I installed the new Ubuntu release on my XPS M1330.
All worked out of the box, except the cpu scaling - which is a little bit annoying, because the laptop fan keeps running since startup.

I checked the forums already,

All required kernel modules (acpi_cpufreq, freq_table, cpufreq_*) are loaded. I installed cpufreqd and cpufrequtils, but the cant change the cpu-speed.
I tried to install the CPU Frequency Scaling Monitor with root privileges, but it didnt work out.

CPU Speed stays at 1,6GHz (got a 2GHz core2) - the only strange thing i found was in /proc/cpuinfo:

ox@oxonsubbook:/var/log$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
stepping        : 13
cpu MHz         : 1600.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3995.05
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
stepping        : 13
cpu MHz         : 1600.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3990.06
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

ox@oxonsubbook:/var/log$ sudo lsmod | grep acpi
acpi_cpufreq           10632  1 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
processor              36232  2 acpi_cpufreq,thermal
ox@oxonsubbook:/var/log$ sudo lsmod | grep cpu
acpi_cpufreq           10632  1 
cpufreq_userspace       6048  1 
cpufreq_powersave       3072  0 
cpufreq_conservative     9608  0 
cpufreq_ondemand       10896  0 
cpufreq_stats           8160  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
processor              36232  2 acpi_cpufreq,thermal
ox@oxonsubbook:/var/log$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
stepping        : 13
cpu MHz         : 1600.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3995.05
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
stepping        : 13
cpu MHz         : 1600.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3990.06
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:


the power management entrys have no value - which seems quite strange to me.

are there any solutions to change cpu-freq on demand?

---

### Post by hanuman1000 on 2007-10-19
My scaling applet is working  (added in the panel) - but the fan keeps going all the time! I have +35 C temp, but only using a few percent of my cpu's processors power (Intel Centrino Duo) 

My scaling is at the lowest 1 GHz (=59 %) - i want to get lower, but it's not possible in the scaling applet?? 

Please help me.

---

### Post by Oxymeron on 2007-10-19
depending on your cpu the scaling might not be able to get under 1GHz

cpufreq-info displays the possible cpu-scaling steps.

---

### Post by Oxymeron on 2007-10-19
I rechecked the configuration and found the following:

The CPU Scaling Monitor can change the scaling gouvernor, but it doesn't have an effect.

/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
and
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq

display always the same value.

---

### Post by Oxymeron on 2007-10-19
ok, i found a workaround:

cpufreq-set -f doesn't work.

but if you set you upper frequence limit to e.g 800Mhz using
cpufeq-set -u 800Mhz

then reset the the upper frequence to the maximum limit using
cpufreq-set -u 2Ghz

the minimum cpu freq. stays at 800Mhz and the maximum switches to 2GHz.

cpufreq-set -d didn't work at all...

---

### Post by jespdj on 2007-10-19
I also have an M1330, with T7300 (2.0 GHz). As far as I can tell, the CPU frequency scaling works correctly on my system.

I added the CPU frequency monitor to the top GNOME panel and most of the time the CPU is running at 800 MHz, it switches to 1.2 GHz and 2.0 GHz if I give the computer something to do.

The T7250 is exactly the same as the T7300, except it has 2 MB instead of 4 MB L2 cache. Strange that it doesn't seem to work correctly on your M1330.

Maybe you have to change a BIOS setting?

---

### Post by resakse on 2007-10-23
> **Oxymeron said:**
> ok, i found a workaround:

cpufreq-set -f doesn't work.

but if you set you upper frequence limit to e.g 800Mhz using
cpufeq-set -u 800Mhz

then reset the the upper frequence to the maximum limit using
cpufreq-set -u 2Ghz

the minimum cpu freq. stays at 800Mhz and the maximum switches to 2GHz.

cpufreq-set -d didn't work at all...

same here, I'm using Compaq Presario M2000 on Gutsy. Please tell me if you found a solution for this, it was working perfectly on Fiesty before..


--- Edit ---

Actually after I set the max and min frequency, 
cpufreq-set -g option, now working perfectly!

anyone know how should I set this on boot, put those command on rc.local?

---

### Post by zakimak on 2008-03-10
For me, it doesn't work :(

> **resakse said:**
> 
anyone know how should I set this on boot, put those command on rc.local?
I think you can insert
> 
cpufreq-set -u 800Mhz
cpufreq-set -u 2Ghz

in /etc/acpi/resume.d/72-acpi-pain.sh at the end before "/etc/acpi/power.sh"

---

### Post by pejobe on 2008-05-03
Read this thread:
[http://ubuntuforums.org/showthread.php?t=389121](http://ubuntuforums.org/showthread.php?t=389121)


This article can also give some information about 
Using Frequency Scaling Governors vs. Using Frequency Scaling Daemons

[http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling)

---

### Post by victorgreen on 2008-05-04
I have scaling enabled and everything works, but for some reason the OS refuses to even try to use my cpu speed. Ive got a T7500 in my X61 and frequency scaling at 800, 1200, 1600, and 2200mhz worked in Fiesty 32 and Gutsy 32. Im now on a clean install of Hardy 64. 

Is this only a 64bit issue??? 

```
~# cpufreq-info
```

> :
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.20 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: powersave, userspace, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 1.20 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz (asserted by call to hardware).
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.20 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: powersave, userspace, ondemand, conservative, performance
  current policy: frequency should be within 800 MHz and 1.20 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz (asserted by call to hardware).


---

