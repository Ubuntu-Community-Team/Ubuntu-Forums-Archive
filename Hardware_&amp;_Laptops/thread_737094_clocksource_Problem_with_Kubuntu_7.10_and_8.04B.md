---
title: "clocksource Problem with Kubuntu 7.10 and 8.04B"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by krakauer4e on 2008-03-27
Hi,

i seem to have a somewhat nasty kernel bug on my machine, it is an AMD X2 running i386 kernel.
Due to powernowd (for cool&quiet ) the clocksource is always unstable. dmesg:
....
Time: hpet clocksource has been installed.
hpet_resources: 0xfed00000 is busy
Clocksource tsc unstable (delta = -71034388 ns)
....
Therefore booting is slow and takes some time. Sadly, the  8.04 Beta behaves the same on my machine.
Any suggestion? Shall i try another clocksource as boot parameter like acpi_pm?
If possible, i'd like to keep acpi and cool&quiet on.
And furthermore am i the only one, having this?
Somehow it seems to affect my keyboard as well, sometimes i cant type at all, sometimes i get a lot of keystokes at once.

regards

---

