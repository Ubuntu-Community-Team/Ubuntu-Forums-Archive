---
title: "Suspend works, but disk restarts immediately."
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by wbrells on 2006-07-04
Hello!

I'm having an unusual (it seems) problem when trying to activate the Suspend to RAM function on my **desktop** system (EPOX 8RGA+ motherboard, Nvidia FX5500 AGP graphics, AMD 2500+ Athlon CPU). I'm running Ubuntu 6.06 "out of the box" and have not installed any special drivers for the Nvidia card. I have activated the ACPI_SLEEP=true line in */etc/default/acpi-support*.

**The Problem:** When I select Suspend, the system seems to go to sleep nicely. However, about 3 seconds after going to sleep, the **disk drive starts up again** and seems to stay constantly active! (That is the disk activity light stays ON constantly.) The video display stays off (displays "No signal") and I have to manually power off the system to recover.

I've played with the various other options in */etc/default/acpi-support*, but nothing seems to help. (BTW, Suspend works fine under Windows 2K.)

Can anyone suggest what might be causing this (partial) "automatic" restart?

Thanks,

Wayne

---

