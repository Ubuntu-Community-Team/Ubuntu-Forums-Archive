---
title: "cpufreqd - CPU &quot;stuck&quot; at lowest speed (ubuntu server)"
date: 2008-06-27
forum: Hardware
---

### Post by matt_garman on 2008-06-27
Hi,

I'm running Ubuntu Server 8.04 (Hardy Heron) on a home-built server.  The motherboard is a Gigabyte GA-EP45-DS3R.  CPU is an Intel Pentium Dual E2160 @ 1.80GHz.

```
$ uname -a
Linux septictank 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux
```

The processor scales back to it's slowest speed (1.2 GHz), then never comes back up, no matter what the load (it seems to get "stuck").  Searching the web, I've seen a number of similar reports, but no resolution.

One thing that's interesting:
```
$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1.20 GHz - 1.80 GHz
  available frequency steps: 1.80 GHz, 1.20 GHz
  available cpufreq governors: powersave, userspace, conservative, ondemand, performance
  current policy: frequency should be within 1.20 GHz and 1.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1.20 GHz - 1.80 GHz
  available frequency steps: 1.80 GHz, 1.20 GHz
  available cpufreq governors: powersave, userspace, conservative, ondemand, performance
  current policy: frequency should be within 1.20 GHz and 1.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz.
```

Note how it says "current policy: frequency should be within 1.20 GHz **and 1.20 GHz**".  Shouldn't that be between 1.2 and *1.80 GHz*?

As this is a server, I don't need anything fancy, such as battery-level specific policies; I'm 100% sure my cooling is adequate, so temperature-based policies are unnecessary as well.  All I want is for the processor to adjust its speed according to load.

Thank you!
Matt

---

### Post by sdennie on 2008-06-27
I've had this happen before as well.  Try this:

```

sudo cpufreq-selector -g userspace
sudo cpufreq-selector -g ondemand

```

That has "unstuck" frequency scaling for me in the past.

---

### Post by matt_garman on 2008-07-02
> **vor said:**
> I've had this happen before as well.  Try this:

```

sudo cpufreq-selector -g userspace
sudo cpufreq-selector -g ondemand

```

That has "unstuck" frequency scaling for me in the past.

Unfortunately, that doesn't have any effect.  (I'm assuming you meant *cpufreq-set* instead of *cpufreq-selector*.)

Interestingly, I can manually change the "frequency should be within" range to be what I expect (see original post), by way of:
```
$ sudo cpufreq-set -c 0 -u "1.8GHz"
$ sudo cpufreq-set -c 1 -u "1.8GHz"
```

But that (still) doesn't make the processor auto-scale under load, even why I try playing with the governor as suggested.

I can also manually force the CPU to the higher speed, ala:
```
$ sudo cpufreq-set -c 0 -f "1.8GHz"
$ sudo cpufreq-set -c 1 -f "1.8GHz"
```

...but then it gets "stuck" at the higher speed.

In short, still no luck!

---

### Post by AlesUbu123 on 2008-07-03
I can also report the same here with kernel 2.6.24-19-generic (i686). The frequency is stuck at the lowest possible value.
Cpufreq-info reports that hardware supports scaling within limits 1.60GHz - 2.13GHz, but it also says
```
current policy: frequency should be within 1.60 GHz and 1.60 GHz
```

None of the advices in this and other threads helped... :(

---

### Post by AlesUbu123 on 2008-07-03
Yay! I solved this according to:

> **Steveway said:**
> Did you try installing powernowd?
If you install it it should remove cpufreqd or whatever you allready have for that purpose installed.
It worked for me after I changed to it.

---

