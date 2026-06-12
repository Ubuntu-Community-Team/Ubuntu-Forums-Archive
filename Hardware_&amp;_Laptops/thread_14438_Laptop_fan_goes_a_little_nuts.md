---
title: "Laptop fan goes a little nuts"
date: 2005-02-07
forum: Hardware &amp; Laptops
---

### Post by marknewlyn on 2005-02-07
Hi all

I got Ubuntu working on my Dell Inspiron 1100. Needed to fix X (add refresh rates) to get full res, added ndiswrapper to get TrueMobile 1300 (Broadcom in disguise) working. Now I just have one concern - my fan seems **extremely** eager and its got me a bit worried.

I found some other posts about fans/heating on the forum and had a look but my laptop has a 2.4GHz Celeron and I managed to bump into the message:

> /etc/init.d/powernowd start
This processor "Intel(R) Celeron(R) CPU 2.40GHz" is known _not_ to support power-saving.
 * Starting powernowd...
 * CPU frequency scaling not supported                                   [ ok ]


I am no expert on kernel modules, hardware devices etc. so can anyone tell me if there is a danger of me damaging the laptop? Is there a solution to the "problem"?

Any advice would be greatly appreciated!

Thanks,

Mark

---

### Post by ulfk on 2005-07-31
i have the same problem on a fujitsu-siemens amilo,
running a 2,4 ghz celeron p4 mobile.
did you find any solutions jet? 

my proc/acpi gives:

cat /proc/acpi/thermal_zone/THRM/
cooling_mode       polling_frequency  state              temperature        trip_points

cat /proc/acpi/thermal_zone/THRM/state
state:                   ok

cat /proc/acpi/thermal_zone/THRM/cooling_mode
<not supported>

cat /proc/acpi/thermal_zone/THRM/polling_frequency
<polling disabled>

cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             75 C

cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           85 C

but no fan controll. i guess the temperature output is not the correct one.

bye ulf

---

