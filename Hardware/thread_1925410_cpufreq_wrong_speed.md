---
title: "cpufreq wrong speed"
date: 2012-02-14
forum: Hardware
---

### Post by qwertyjjj on 2012-02-14
I just upgraded to Ocelot and suddenyl my CPU has been throttled to 600 instead of max 1.73GHz.
The governor lists performance but is not listing the corretc max speeds.
I tried setting the processor.ignore_ppc=1 in the grub but that has not helped.
ANy ideas how I can get this working?
The drive is also incorrect!

cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  **driver: p4-clockmod**
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  hardware limits: 75.0 MHz - 600 MHz
  available frequency steps: 75.0 MHz, 150 MHz, 225 MHz, 300 MHz, 375 MHz, 450 MHz, 525 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within **75.0 MHz and 600 MHz**.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 600 MHz.
  cpufreq stats: 75.0 MHz:0.00%, 150 MHz:0.00%, 225 MHz:0.00%, 300 MHz:0.00%, 375 MHz:0.00%, 450 MHz:0.00%, 525 MHz:0.00%, 600 MHz:100.00%

---

### Post by bluexrider on 2012-02-14
> **qwertyjjj said:**
> I just upgraded to Ocelot and suddenyl my CPU has been throttled to 600 instead of max 1.73GHz.
The governor lists performance but is not listing the corretc max speeds.
I tried setting the processor.ignore_ppc=1 in the grub but that has not helped.
ANy ideas how I can get this working?
The drive is also incorrect!

cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [EMAIL="cpufreq@vger.kernel.org"]cpufreq@vger.kernel.org[/EMAIL], please.
analyzing CPU 0:
  **driver: p4-clockmod**
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  hardware limits: 75.0 MHz - 600 MHz
  available frequency steps: 75.0 MHz, 150 MHz, 225 MHz, 300 MHz, 375 MHz, 450 MHz, 525 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within **75.0 MHz and 600 MHz**.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 600 MHz.
  cpufreq stats: 75.0 MHz:0.00%, 150 MHz:0.00%, 225 MHz:0.00%, 300 MHz:0.00%, 375 MHz:0.00%, 450 MHz:0.00%, 525 MHz:0.00%, 600 MHz:100.00%
Find the correct driver. This one has its limitations as it states but you realize this already.
What were you using before?

BTW just because the **driver: p4-clockmod **is stating the processor speed incorrectly doesn't mean that the processor is truly running at that speed.

This may help diag the problem, post please

```
hwinfo --cpu
```

---

### Post by qwertyjjj on 2012-02-14
No, it really is running slowly, everything is very sluggish.
I tried running sudo modprobe speedstep-smi but it didn't help, it didn;t change the driver in the cpufreq-info information either.

hwinfo --cpu
> hal.1: read hal dataprocess 3424: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
01: None 00.0: 10103 CPU                                        
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 6.13.8 "Intel(R) Pentium(R) M processor 1.73GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,mtrr,pge,mca,cmov,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,tm,pbe,nx,up,bts,est,tm2
  Clock: 600 MHz
  BogoMips: 1595.82
  Cache: 2048 kb
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by Yellow Pasque on 2012-02-14
blacklist p4-clockmod?

---

