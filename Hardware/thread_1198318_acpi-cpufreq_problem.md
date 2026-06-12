---
title: "acpi-cpufreq problem"
date: 2009-06-27
forum: Hardware
---

### Post by gaboro on 2009-06-27
hiya,

i figured out that since a while cpufreq does not work on my samsung x20 (centrino 1,86) laptop anymore. 
after booting, cpufreq-info says that for the ondemand governor the freq should be within 1.87 GHz and 1.87 GHz - so it works on max. freq.

if i reload acpi-cpufreq saying [FONT="Courier New"]sudo rmmod acpi_cpufreq[/FONT] and [FONT="Courier New"]sudo modprobe acpi-cpufreq[/FONT] it works again, the range for the same governor is 800 MHz - 1.87 GHz, stepping works like charm.

i am using ubuntu 8.10.

do you have any clue? 
any help is welcome.

---

