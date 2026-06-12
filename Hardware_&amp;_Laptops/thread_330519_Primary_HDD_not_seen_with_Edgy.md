---
title: "Primary HDD not seen with Edgy"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by devnull-fr on 2007-01-03
Hi there and happy new year,

I've bought an ASUS P5B-E Mobo and installed it with Win XP w/o any problem.

My config:
P5BE - Core 2 6400 - 1 Go DDR2
1 HDD MAxtor 160Go SATAII on ICH8R (RAID mode config in Bios) Sata port 1 on mobo
2 HDD Hitachi RAID 0 on ICH8R (SATA ports 3 & 4 on mobo)
1 DVD burner Phillips (IDE) on Jmicron Ctrl (IDE mode)

The problem is that Ubuntu does not detect my primary HD (Maxtor).
A "sudo fdisk -l" gives me sda & sdb for Hitachi drives only.

I've tried Alternate 6.10 but same result. I've also tried with System Rescue CD and all
my drives are well detected !

--------
Edit : Tried with Feisty alternate (2.6.20-generic from january 3rd), chipset ICH8R, jmicron and even Attansic L1 are well recognised (but last one still not loaded).
Now, installer fails mounting my DVD and does not see it. May be 'udev' would help ?
--------

Could someone give me some light on this ? any ideas ? 
TIA
Devnull-fr

---

