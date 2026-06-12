---
title: "cpufrequtils gets stuck at lowest CPU frequency after laptop wakes up"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by softtower on 2007-09-09
I have IBM ThinkPad T60 with Core 2 Duo 2Gz CPU. I configured cpufrequtils to use "ondemand" governor and my frequency scales from 1Gz to 2Gz quite nicely.

However, after I put the laptop in standby mode and then wake it up, cpufrequtils gets stuck in the lowest possible frequency. This is what cpufrequtils-info reports now:

>   current policy: frequency should be within 1000 MHz and 1000 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.


I've been trying to call cpufreq-set with various parameters, but it reports no errors but does not do anything. If I power laptop down (or reboot) - then it starts working again and it scales up to 2Gz.

---

### Post by softtower on 2007-09-09
Another issue is that my governor (after I reboot) is always set to "ondemand" even though I configured it to use "conservative".

My /etc/default/cpufrequtils looks like this:
```
ENABLE="true"
GOVERNOR="conservative"

```

---

### Post by softtower on 2007-09-19
I found how to fix this problem although I still believe this is a bug in one of kernel modules.

I commented out all governors from my /etc/modules file, leaving only "main" module:
acpi-cpufreq

The modules I got rid of were:
cpufreq_ondemand
cpufreq_conservative
cpufreq_userspace

Now everything works and I have two gonvernors available: "conservative" and "ondemand" even though those modules are not included in /etc/modules I guess they are compiled into the kernel.

---

