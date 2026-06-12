---
title: "Problems with cpu-freq scaling."
date: 2009-09-22
forum: Hardware
---

### Post by he-man on 2009-09-22
Hello. I'm going crazy to make frequency scaling work in ubuntu 9.10.
I've got a core 2 duo E6300 processor in a desktop PC, and the 64-bits version of ubuntu installed.

I've never been able to make the cpufreq scaling work either in 9.10 or 9.04, 8.0... etcetera.

cpufreq-info output:

cpufrequtils 005: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU


I installed cpufreq-utils and the daemon. The problem is that I cannot load the module for my processor because it does not exist.

I looked at my bios to see if I had power management active. I had: it's called acpi and acpi-2.0 or something similar. 

I tried everything, looked for hints and tutorials everywhere, but I can't find how to make it work.

Any clues, please? Thanks in advance.

---

