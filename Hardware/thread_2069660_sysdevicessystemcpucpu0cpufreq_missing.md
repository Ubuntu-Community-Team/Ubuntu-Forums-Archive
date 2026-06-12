---
title: "/sys/devices/system/cpu/cpu0/cpufreq missing"
date: 2012-10-11
forum: Hardware
---

### Post by Sworddragon on 2012-10-11
My system has now an AMD Phenom II X6 1045T but the problem is it is always on 800 MHz on every core even if the system is under heavy workload. I have already en/disabled Cool'n'Quiet in the BIOS but there is no difference.

I have installed cpufrequtils to solve this problem but "Loading cpufreq kernel modules..." fails. After debugging the script it loads successfully the module powernow-k8 but it fails on checking for files in /sys/devices/system/cpu/cpu0/cpufreq.

There are now 2 possibilities:

1. Something is not correctly configured on my system.

2. My mainboard doesn't fully support the processor.


My mainboard is this: [http://www.asrock.com/mb/overview.asp?model=n68-s](http://www.asrock.com/mb/overview.asp?model=n68-s)
It is an AM2 mainboard which supports AM2+ and AM3 processors. The BIOS is up to date (2.10) but maybe there is a problem with the mainboard. Maybe somebody has an idea if the problem can be solved for me without changing the mainboard.

---

### Post by Sworddragon on 2012-10-12
I have tested some different settings in the BIOS and only one of them made a difference. Setting the multiplier from auto to manual (with the default values) will run the processor with 2.7 GHz. But /sys/devices/system/cpu/cpu0/cpufreq is still missing and the processor doesn't change the frequency down- or upwards if needed.

I have switched back to my AMD Athlon 64 X2 and the directory exists then. The processor does even scale his frequency from 2 GHz to 1 GHz on idle. It seems this is really an issue with my mainboard and newer processors (even if officially supported).

---

