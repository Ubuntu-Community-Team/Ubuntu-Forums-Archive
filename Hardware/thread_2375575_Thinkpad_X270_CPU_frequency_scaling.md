---
title: "Thinkpad X270 CPU frequency scaling"
date: 2017-10-25
forum: Hardware
---

### Post by ditsara on 2017-10-25
Hi, I'm running Ubuntu 16.04 on a Thinkpad X270, and it seems that CPU frequency scaling is always stuck at 100%. The MATE applet shows 100% whether I have performance or powersave selected, and the machine always seems to be hot. I've searched in the forums and online, but I haven't been able to find anything related to this issue. Can someone help point me in the right direction?

Here's my output of cpufreq-info, if it helps

```

cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 0.97 ms.
  hardware limits: 400 MHz - 3.10 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 400 MHz and 3.10 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 3.10 GHz.
analyzing CPU 1:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 0.97 ms.
  hardware limits: 400 MHz - 3.10 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 400 MHz and 3.10 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 3.10 GHz.
analyzing CPU 2:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 2
  CPUs which need to have their frequency coordinated by software: 2
  maximum transition latency: 0.97 ms.
  hardware limits: 400 MHz - 3.10 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 400 MHz and 3.10 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 3.10 GHz.
analyzing CPU 3:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 3
  CPUs which need to have their frequency coordinated by software: 3
  maximum transition latency: 0.97 ms.
  hardware limits: 400 MHz - 3.10 GHz
  available cpufreq governors: performance, powersave
  current policy: frequency should be within 400 MHz and 3.10 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 3.10 GHz.



```

---

### Post by ditsara on 2017-10-25
Okay, I think I found the answer here: [https://askubuntu.com/questions/812530/cpu-frequency-scaling-not-working-as-intended-on-vanilla-ubuntu-16-04](https://askubuntu.com/questions/812530/cpu-frequency-scaling-not-working-as-intended-on-vanilla-ubuntu-16-04)

Basically I added GRUB_CMDLINE_LINUX_DEFAULT="intel_pstate=disable" as per the link above and my CPU frequency seems to be scaling correctly with load now. I'll continue to monitor CPU temps / frequency and post again if I encounter any problems.

---

### Post by Doug S on 2017-10-27
Could you tell us which kernel version you are using and your cpu model. Example:
```
$ [COLOR="#FF0000"]uname -a[/COLOR]
Linux s15 4.14.0-rc6-stock #315 SMP Mon Oct 23 08:21:03 PDT 2017 x86_64 x86_64 x86_64 GNU/Linux
$ [COLOR="#FF0000"]grep "model name" /proc/cpuinfo[/COLOR]
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz

```As I mentioned on the answer you referenced, this would not account for a hotter computer.
Also, that specific issue with the intel_pstate driver has been fixed (finally), but I have no idea if it has been backported to earlier kernels.

---

### Post by Yellow Pasque on 2017-10-27
If the CPU is always running at full speed/voltage, it would account for a hotter system. It's going to be more noticeable on a laptop.

---

### Post by Doug S on 2017-10-27
> **Temüjin said:**
> If the CPU is always running at full speed/voltage, it would account for a hotter system. It's going to be more noticeable on a laptop.No, that is not always true. If it does run at a faster cpu speed, when it is running, it then also completes its work faster and therefore can spend more time is deep idle states, consuming little or no energy.

---

### Post by ditsara on 2017-12-06
For completeness:

```

$ uname -a

[COLOR=#000000]Linux losfeliz 4.10.0-40-generic #44~16.04.1-Ubuntu SMP Thu Nov 9 15:37:44 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

[/COLOR]$ grep "model name" /proc/cpuinfo

model name    : Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
model name    : Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
model name    : Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
model name    : Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz

```

What kernel version was the intel_pstate issue fixed in (or can you point me to a reference)?

---

### Post by Doug S on 2017-12-07
> **ditsara said:**
> 
What kernel version was the intel_pstate issue fixed in (or can you point me to a reference)?
It was this commit:
```
commit 553953453b4b64fbccba31691257d006cee36613
Author: Rafael J. Wysocki <rafael.j.wysocki@intel.com>
Date:   Wed Mar 22 23:53:54 2017 +0100

    cpufreq: intel_pstate: Use load-based P-state selection more widely

    Extend the set of systems for which intel_pstate will use the
    "powersave" P-state selection algorithm based on CPU load in the
    active mode by systems with ACPI preferred profile set to "tablet",
    "appliance PC", "desktop", or "workstation" (ie. everything with a
    specified preferred profile that is not a "server").

    Signed-off-by: Rafael J. Wysocki <rafael.j.wysocki@intel.com>

```It would have been kernel 4.12. And later on it was made the only option (i.e. servers also).

---

### Post by Doug S on 2017-12-07
Actually, a 7th generation i5 should be using HWP (HardWare P-state control) by default, so the software control algorithm shouldn't matter.

---

### Post by ditsara on 2018-02-03
Going to go ahead and mark as solved. I used ukuu to update to the latest kernel (4.15) and everything seems to be working smoothly now!

---

