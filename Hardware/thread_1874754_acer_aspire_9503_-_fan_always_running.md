---
title: "acer aspire 9503 - fan always running"
date: 2011-11-03
forum: Hardware
---

### Post by discord on 2011-11-03
The fan on my aspire 9503 is always running, after installing lubuntu 11.10 . I tried loading the acerhdf module, but i get errors.

sudo modprobe acerhdf
FATAL: Error inserting acerhdf (/lib/modules/3.0.0-12-generic/kernel/drivers/platform/x86/acerhdf.ko): Invalid argument

islandjoe@islandjoe-Aspire-9500:~$ sudo echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode
bash: /sys/class/thermal/thermal_zone0/mode: No such file or directory

Can anybody suggest how I can get the fan to only activate when under load. The computer is cold, but it's damn annoying. It sounds like an aircraft preparing for takeoff.

---

### Post by discord on 2011-11-04
solved, flashing the bios fixed the issue...

---

