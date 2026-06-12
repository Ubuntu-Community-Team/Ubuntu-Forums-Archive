---
title: "Dual Boot Sata Raid - fakeraid / dmraid ???"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by matsie on 2006-01-28
Hi
I searched in various boards and I am trying to install a Dual Boot environment.

_Current Situation:_
AMD64 K8V
- 2 Sata 160 GB HDD Raid0
- HDDs are recognized as 1 HDD of 320 GB and partioned as follows:
-- sda1: C: 10 GB Win XP NTFS
-- sda2: D: E: F: G: <-- together 260 GB FAT32
-- **sda3**: Linux 50 GB EXT3
- Windows XP currently running

_Goal:_ 
- Install Ubuntu over Win XP

What I did so far: 
- using the ADM64 LiveCD I downloaded dmraid that maps and recognizes the partitions as described above. Without dmraid Ubuntu recognizes only the 2 physical HDDs sda and sdb of 160 GB each. 
- in order to setup sda3, the linux partition, I followed principally the howto of the following site [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto). 
- As for grub I had to adjust the geometry. 
- I had to edit fastb and menu.lst manually

_Interim Result:_
- The grub loader shows up on starting the PC: ok
- When I try to start Ubuntu, the boot procedure begins (on hd0,2 referring to sda3).

_Problem:_
- Suddenly the boot loading procedure aborts, stating error messages as follows:
-- XXXX ports closed, and then 
-- **/bin/sh: can't access tty; job control turned off**

Any hints how to solve this issue are welcome. 
Regards, 
Mat

---

