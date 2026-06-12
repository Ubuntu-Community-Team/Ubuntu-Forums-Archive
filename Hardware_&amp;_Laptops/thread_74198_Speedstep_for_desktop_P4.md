---
title: "Speedstep for desktop P4?"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by matthias_k on 2005-10-11
Hi,

I am running Hoary on my notebook and I am using some facility to throttle the CPU frequency (I think it's speedstep, it's a Centrino CPU).

Now, on my desktop, I run a Pentium 4 3.0GHz, but I feel it's a waste of energy to always run it at full speed, since I'm not actually running any demanding applications. So, I was wondering if a Pentium 4 can also be throttled using some CPU-speed daemon?

Does it work the same as on the notebook or does this kind of power management only work with mobile CPUs?

Thanks in advance,
Matthias

---

### Post by matthias_k on 2005-10-12
Anyone? ^^

---

### Post by matthias_k on 2005-10-25
*bump*

---

### Post by Mizzou_Engineer on 2005-11-06
[QUOTE=matthias_k]Hi,

I am running Hoary on my notebook and I am using some facility to throttle the CPU frequency (I think it's speedstep, it's a Centrino CPU).

Now, on my desktop, I run a Pentium 4 3.0GHz, but I feel it's a waste of energy to always run it at full speed, since I'm not actually running any demanding applications. So, I was wondering if a Pentium 4 can also be throttled using some CPU-speed daemon?

Does it work the same as on the notebook or does this kind of power management only work with mobile CPUs?

Thanks in advance,
Matthias[/QUOTE]

I know that the only Intel desktop CPUs that support frequency scaling are the Pentium D 830, 840, and 840EE. The 820 does not. The rest all run at full clock speed no matter what. However, all new Intel dual-core chips are going to have Enhanced Intel Speedstep Technology (like the Centrinos) to keep the power draw down. 

All P4 chips will *appear* to throttle back if they overheat, but that is only because the chips, to prevent melting, will eat two out of three clock cycles. You don't want that!

---

### Post by matthias_k on 2005-11-07
Okay, thanks for clearing up.

---

### Post by aminalshmu on 2005-11-10
My Prescott P4 2.8 ghz can be clocked/speedstepped, the drivers for this are in the mainline kernel. In my ubuntu kernel (686 2.6.12.16) the p4_clockmod module is compiled by default. Just do a "sudo modprobe p4_clockmod" and then you can run powernowd or whatever cpufreq userspace utility you would like...

[http://www.kernel.org/pub/linux/utils/kernel/cpufreq/cpufreq.html](http://www.kernel.org/pub/linux/utils/kernel/cpufreq/cpufreq.html)

Intel Pentium4/Xeon clock modulation (p4-clockmod)

is listed under "supported hardware" so I think any P4 should be able to use it.

---

### Post by djkork on 2005-11-21
[QUOTE=Mizzou_Engineer]I know that the only Intel desktop CPUs that support frequency scaling are the Pentium D 830, 840, and 840EE. The 820 does not. The rest all run at full clock speed no matter what. However, all new Intel dual-core chips are going to have Enhanced Intel Speedstep Technology (like the Centrinos) to keep the power draw down. 

All P4 chips will *appear* to throttle back if they overheat, but that is only because the chips, to prevent melting, will eat two out of three clock cycles. You don't want that![/QUOTE]

What are you talking about??? Since PIV all intel processors support frecuency scaling including all celeron (p4 based...),centrino, Desktop or mobile P4 CPUs.... and all of them are supported under linux....
P4 family  frecuency scaling is supported by the X86_P4_CLOCKMOD module..
and you can control the frequency as you want.... 
-userspace governor + cpufreq-set .... to set it up manually
-userspace governor + powernowd..... to let powernow to decide best freq speed (powernodw changes de freq dinamically adapting it to your progs demand)
-ondemand governor.... let the kernel decide best freq ( adapting it dinamically.....)

there are more governors... and userspace freq controllers....

Now i have a PIV 2.8 with userspace governor controlled by powernowd 

> analyzing CPU 0:
  driver: p4-clockmod
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 350 MHz - 2.80 GHz
  available frequency steps: 350 MHz, 700 MHz, 1.05 GHz, 1.40 GHz, 1.75 GHz, 2.10 GHz, 2.45 GHz, 2.80 GHz
  available cpufreq governors: powersave, conservative, ondemand, userspace, performance
  current policy: frequency should be within 350 MHz and 2.80 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 2.80 GHz.

---

### Post by matthias_k on 2005-11-22
Unfortunately, my CPU (P4 3.0) only seems to support frequencies down to 2.25 GHz:
> 
2250000
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq (END) 

Strange, that doesn't make such a big difference.

---

### Post by djkork on 2005-11-22
[QUOTE=matthias_k]Unfortunately, my CPU (P4 3.0) only seems to support frequencies down to 2.25 GHz:

Strange, that doesn't make such a big difference.[/QUOTE]

If you are using P4clock_mod see if the module is detecting N60 errata....
I explain about it [here]("http://www.ubuntuforums.org/showthread.php?p=509795#post509795")

---

