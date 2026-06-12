---
title: "One of my cores is constantly under full load"
date: 2008-11-25
forum: General Help
---

### Post by NCLI on 2008-11-25
I left my PC running overnight while downloading some torrents, and when I check out the CPU usage next morning, I notice that Core0 is under full load, even though I'm running nothing but Deluge. I reboot the computer, but when I log in, the System Monitor still shows that one core is fully loaded.

---

### Post by RMSe17 on 2008-11-25
I would say the first step is to check what is using up the whole core.  One of the ways to do this is to go to System Menu -> Administration -> System Monitor,  and check in the Processes tab.

---

### Post by NCLI on 2008-11-25
> **RMSe17 said:**
> I would say the first step is to check what is using up the whole core.  One of the ways to do this is to go to System Menu -> Administration -> System Monitor,  and check in the Processes tab.

The worst offender I can find in there is System Monitor itself, which uses from 3% to 7%. My core temps don't seem to match the heavy load Core0 should be under. Core0 is 51C, and Core1 is 49C, which are very acceptable idle temps for my overclocked E8500. 

Could it be a bug in System Monitor?

EDIT: I just booted XP to check whether it reported the same strange CPU usage. It didn't, which means this is definitely a problem with Ubuntu.

---

