---
title: "[SOLVED] Dell inspirion 6000 cpu scaling"
date: 2008-11-22
forum: Hardware
---

### Post by mouseboyx on 2008-11-22
My Inspirion 6000 is stuck at 600mhz, i have no battery so i have no intentions of saving power, i just want to bump it up to 1.7Ghz, i enabled root privileges for the scaling monitor but it will not change it it just stays at 600mhz no matter what you do.

1.7ghz is one of the available speeds

```

mouse@I6000:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 600 MHz - 1.70 GHz
  available frequency steps: 1.70 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: ondemand, powersave, userspace, conservative, performance
  current policy: frequency should be within 600 MHz and 600 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 600 MHz.

```

I want to know what is wrong and how i can bump it up from this painfully slow speed.

---

### Post by sdennie on 2008-11-22
Try:

```

sudo cpufreq-selector -g ondemand

```

That should make it scale between the min and max speed (it should do it so quickly that you will never notice when it's sitting at min speed).  If that works, there are ways to make that permanent like adding it to /etc/rc.local or, if you suspend/resume the machine, to the various pm-utils locations.

---

### Post by mouseboyx on 2008-11-22
thanks, but 
```

current policy: frequency should be within 600 MHz and 600 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.

```

Now it just says that the scaling is using governor "ondemand", yet the frequency should be within 600mhz to 600mhz, when running strenuous applications, it still stays at 600mhz...

---

