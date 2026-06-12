---
title: "Cool'n'Quiet"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by The Devil Is A Squirrel on 2006-06-25
Hi everybody

First of all, I'm a Linux newbie (started with Knoppix then FC4&FC5 but not satisfied) and I'm really happy with Ubuntu!

There is only one problem: It seems that the Cool'n'Quiet feature from AMD does not work in Ubuntu (or any Linux?) nor does it detect the second core (FC5 does show in the system monitor the second core...Ubuntu does not) and the overall CPU-Load is quit high.

I've installed the 386 version of Ubuntu with all updated...any further information required?

Thanks and greetz from Switzerland

---

### Post by mips on 2006-06-25
For the second core you need to use a SMP kernel.

---

### Post by hajk on 2006-06-26
Cool'n'Quiet is specific for AMD processors, so you should install either the k7 or the k8 kernel for that. Both kernels have SMP configured, the k7 kernel is 32-bits while the k8 kernel is 64-bits. You should check out some of the discussions on the pros and cons of these in the Dapper 64-bit sub-forum. 

Note: you may also need an up-to-date BIOS for your motherboard to make the Cool'n'Quiet feature work.

---

### Post by The Devil Is A Squirrel on 2006-06-26
Thanks for your hints!

I have installed now the 686-smp-kernel with powernowd running.

cpufreq-info shows, that the speed steeping works.
```
$ sudo cpufreq-info
cpufrequtils 0.4: cpufreq-info (C) Dominik Brodowski 2004
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.00 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz (asserted by call to hardware).
analyzing CPU 1:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.00 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz (asserted by call to hardware).

```

Although I can see that the system uses between 20 and 30 watt more than windows xp (idle mode) and now I believe it's not a cpu problem but rather a gpu problem. How could I track this? Or does anyone know more about that?

---

### Post by asterus on 2007-10-31
> **The Devil Is A Squirrel said:**
> Thanks for your hints!

I have installed now the 686-smp-kernel with powernowd running.

cpufreq-info shows, that the speed steeping works.
```
$ sudo cpufreq-info
cpufrequtils 0.4: cpufreq-info (C) Dominik Brodowski 2004
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.00 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz (asserted by call to hardware).
analyzing CPU 1:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.00 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz (asserted by call to hardware).

```

Although I can see that the system uses between 20 and 30 watt more than windows xp (idle mode) and now I believe it's not a cpu problem but rather a gpu problem. How could I track this? Or does anyone know more about that?

I have absolutely the same problem. Can someone help me too?

---

