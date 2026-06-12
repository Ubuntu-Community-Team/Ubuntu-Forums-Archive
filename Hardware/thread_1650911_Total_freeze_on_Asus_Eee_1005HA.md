---
title: "Total freeze on Asus Eee 1005HA"
date: 2010-12-22
forum: Hardware
---

### Post by rowan_m on 2010-12-22
I've been having a problem with my Asus Eee 1005HA where it consistently locks up on certain tasks. Specifically, I can trigger it by importing a large photo folder on Shotwell or certain flash applets. I say "total freeze" because the system is totally unresponsive, even to the magic SysRq key combinations.

I can solve this issue by forcing the CPU governor to be "powersave" at all times via manually altering /etc/init.d/ondemand but that seems a bit poor.

So, questions are: has anyone else experienced this and does anyone know how I can capture any information on the lock?

(This has happened across multiple Ubuntu versions, kernels, grub boot opts, etc. the cpufreq governor definitely seems to be the culprit.)

---

