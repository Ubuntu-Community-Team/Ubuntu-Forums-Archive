---
title: "problem with CPU scaling (very bad)"
date: 2008-07-23
forum: Hardware
---

### Post by ozp on 2008-07-23
With no apparent reason, the CPU speed drops to 800 mhz and stay there for a while. Then somethimes the system freese or the speed goes up again.

Its bad because the computer get too slow and start to get too hot.

Ive read the forum here and found no solution or no related problem like mine

System: ubuntu 8.04 (upgraded from 7.10)
Computer: dell D830

Where to start to solve this?

```

ozp@ozp-d830:~$ cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, userspace, powersave, ondemand, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, userspace, powersave, ondemand, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.

```

Look above, even after I change the governor to PERFORMANCE the speed is set to 800 and cannot change.

And then after a while its goes back to what it should be, but in the mean time the computer is a OLD TURTLE and frezze to death

The only clue I have about some possible reason is that this problem happends when I have deluge mplayer on. (I dont know if this is related or not)

 I have this installed with root privileges running : CPU Frequency Scaling Monitor 2.22.2

please help

---

### Post by Dark_Stang on 2008-07-23
Your processor isn't going to run at a full 2GHz all the time. It's only going to run as fast as it needs to. I have a dual core AMD Turion TL-58 processor in my laptop, and it normally runs at 800MHz on both cores. It's range is 800MHz to 1.9GHz. 

Now if it isn't scaling when it should, that is another issue. As is the freezing. This may indicate some software issues or possibly a bad processor.

---

### Post by sdennie on 2008-07-23
It could be the case that the lowered frequency is not causing the heat but instead that the heat is causing the lower frequency.  I would verify that all the fans on the machine are running and that nothing is obstructing the vents on the machine (especially dust).  Using compressed air to clean the vents of a laptop at least once a month can really help these sorts of problems.

---

### Post by ozp on 2008-07-24
Vor, I'll clean the FAN and see if it works

I think that may be the heat that is causing the problem. Also because the problem happends most at my home, when I use the computer sitting on the top of a "pillow"

The weird thing is that this problem began after the 8.04 upgrade. Before that is never happend

---

### Post by evets25 on 2008-07-24
Yes, well that might be part of your problem. I tell this to everyone I know who owns a laptop or is thinking of getting one: whenever you use it, make sure that there is sufficient room on the bottom of the computer and sides for air flow, and make sure the vents aren't covered so that the computer can pump the heat out and suck cool air in. Otherwise, your computer will overheat, slow down, and eventually stop working altogether as various components take heat damage over time. **Do not rest your laptop on a pillow!** The pillow conforms to the shape of your laptop, effectively covering the vents, making it REALLY easy to overheat!

---

### Post by ozp on 2008-07-24
I feel like the most newbie ever....

Using compresseed air on the notebook fan made the temperadure drop 10, 15 degrees or more.

I think the cpu speed wont drop again

---

