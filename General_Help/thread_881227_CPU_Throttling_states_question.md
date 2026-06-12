---
title: "CPU Throttling states question"
date: 2008-08-05
forum: General Help
---

### Post by Krupski on 2008-08-05
Hi all,

My little server box has an Intel Core 2 Duo E6700 CPU in it. The boot logs contain these lines:

ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: Processor [CPU1] (supports 8 throttling states)


However, using either the POWERNOWD daemon or ACPI-CPUFREQ (and the "conservative" governor), the CPU only seems to have 5 different clock frequencies that it's throttled to:

2660000 2394000 2128000 1862000 1596000

I've even run a little shell script to copy the contents of '/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq' file at 10 times per second while loading the machine with tasks.

Sure enough, the CPU speed only switches between these 5 states.

So... the CPU supports 8 throttling states, but the OS (Ubuntu Server 8.04.1 64 bit) only uses 5.

Anyone know why?

Thanks!

-- Roger

---

### Post by kuja on 2008-08-05
I think it gets its available frequences from the /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies file ... I don't know what your system lists there, but my laptop only lists 5. I'm thinking it's less of an issue of what powernowd is doing and more of an issue with the kernel's cpufreq driver maybe?

---

### Post by Krupski on 2008-08-05
> **kuja said:**
> I think it gets its available frequences from the /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies file ... I don't know what your system lists there, but my laptop only lists 5. I'm thinking it's less of an issue of what powernowd is doing and more of an issue with the kernel's cpufreq driver maybe?

Yes, those 5 frequency entries are in .../scaling_available_frequencies, but I don't know how they GOT there or why there are 5 instead of 8.

Each entry is 266000 apart (which is 10% of the max).

I could just experiment and change those files and see what happens... but I was hoping that someone would know (i.e. I'm lazy). :)

I wonder HOW the CPU clock speed is changed on the hardware level... does the PLL divider get programmed... or are there a few input pins that change it..?

All in all, it doesn't even matter... I'm just curious.

:lolflag:

---

