---
title: "One CPU Core &quot;Missing&quot; when resuming from Suspend in C2D system"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by fulat2k on 2008-03-07
Hi folks,

I'm using a Dell Latitude D630 equipped with C2D CPU.  Upon normal startup, both CPU cores are detected properly.  However, after resuming from suspend, one CPU core goes missing.  Below is the output from cpufreq-info:

[PHP]
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 1.80 GHz
  available frequency steps: 1.80 GHz, 1.80 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: powersave, conservative, ondemand, userspace, performance
  current policy: frequency should be within 800 MHz and 1.80 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
[/PHP]

Any idea if I need to disable any modules in acpi-default file?


Thanks.

---

### Post by fulat2k on 2008-03-11
hi folks,

ne ideas?


thanks.

---

### Post by marteus on 2008-04-16
I have the same problem with hardy on a Dell m1330 (with a penryn cpu)

---

### Post by marteus on 2008-04-16
Seems there is a bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/183033/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/183033/)

but no fix yet.

---

