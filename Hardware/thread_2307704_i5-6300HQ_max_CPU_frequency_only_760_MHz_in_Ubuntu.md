---
title: "i5-6300HQ max CPU frequency only 760 MHz in Ubuntu 15.04"
date: 2015-12-27
forum: Hardware
---

### Post by sai10 on 2015-12-27
**TL;DR: CPU rated for 2.3 GHz (3.2 GHz Turbo), works fine in Windows, but does not exceed 759 MHz under full load in Ubuntu**

I have a Dell Inspiron i7559 laptop with a Core i5-6300 HQ and an NVIDIA GTX960M GPU. I have installed Ubuntu 15.04 on it, and I've been noticing that the CPU performance is much slower than I expected, especially when I run make even when using all four threads. Lintian takes extremely long amounts of time when checking packages etc.

So I downloaded Super Pi and ran a single threaded benchmark. For 1M digits of pi, it takes 25-26 seconds, whereas my Windows install on the same computer takes 12-13 seconds. Under load, indicator-cpufreq only shows 0.76 GHz.

Something is also off with cpufreq-info, it reports steps of 1 MHz and 759 MHz? That doesn't make sense to me; here's the report for CPU0:
[FONT=courier new]
    analyzing CPU 0:
      driver: acpi-cpufreq
      CPUs which run at the same hardware frequency: 0
      CPUs which need to have their frequency coordinated by software: 0
      maximum transition latency: 10.0 us.
      hardware limits: 1000 kHz - 759 MHz
      available frequency steps: 759 MHz, 1000 kHz
      available cpufreq governors: conservative, ondemand, userspace, powersave, performance
      current policy: frequency should be within 1000 kHz and 759 MHz.
                      The governor "ondemand" may decide which speed to use
                      within this range.
      current CPU frequency is 1000 kHz.
      cpufreq stats: 759 MHz:19.19%, 1000 kHz:80.81%  (673)[/FONT]


This is really a problem for me, and I don't know why this is happening. Any suggestions or pointers would be very helpful, thank you!

EDIT: I ran these

[FONT=courier new]$lshw -c cpu
*-cpu                   
       product: Intel(R) Core(TM) i5-6300HQ CPU @ 2.30GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       size: 1MHz
       capacity: 759MHz
       width: 64 bits[/FONT]



     [FONT=courier new]$ cat /sys/devices/system/cpu/cpu0/cpufreq/bios_limit
     759000[/FONT]

I do not know the implications of "bios_limit", because it seems to be fine in Windows, but is there a way to change this safely so that I can use both the standard 2.3 GHz and the Intel Turbo speeds (Turbo goes up to 3.2 on this one)?

---

