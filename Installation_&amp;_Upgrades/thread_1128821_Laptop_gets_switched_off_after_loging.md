---
title: "Laptop gets switched off after loging"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by kunaalatrehan on 2009-04-18
Hi 
I have a very strange problem 
I have Toshiba Satellite M35X-S329 laptop
with  Intel Pentium M Processor 725 1.6GHZ

Till few days back I was running Window XP and Ubuntu 7.0.4 
with dual boot .I had no issues at atll.

Issue started when I formatted and removed all the partitions
I first installed Ubuntu 8.10.It got installed 
However after booting up and logging in .
My laptop gets switched off automatically 

THen I again cleaned up the laptop and installed 8.0.4
Same thing happens
It gets logged in and then it gets switch off automatically 

However if I install Windows XP no issues at all 
I want to have only Ubuntu as O/S

Please help me out what I should do to solve this problem

Thanks
Kunaal A Trehan

---

### Post by lemming465 on 2009-04-19
If you have access to a newer version of Ubuntu you could try 8.10 or 9.04 RC.  Your symptom sounds like ACPI power management bugs; later kernels might have better workarounds.  You could try booting with some combination of *acpi=off noapic nolapci* and see if that helps.  You could also try turning off power management options in the BIOS, though that might impact your battery life.

---

### Post by iSKUNK! on 2009-11-11
A similar model of laptop (M35X-S149) has the same problem, due to a buggy ACPI implementation in the BIOS. See [this bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/242400) for details.

Upgrading the BIOS fixed the problem for that model, and may do the same for yours.

---

