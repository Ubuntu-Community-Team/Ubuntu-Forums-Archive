---
title: "quad boot trouble"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by Al-Man on 2009-09-15
Hi I wonder if anyone could help me with a booting problem with grub (this may not be a possible thing to do). I have 2 PATA hard drives in my computer the first Master hd0 has a windows XP NTFS partition followed by an ext4 partition with Ubuntu installed and then a swap partition and finally a NTFS data partition. The second drive is a slave and has XP in stalled on a NTFS partition followed by a ext4 partition with Kubuntu installed followed by a swap partition. My problem is if I set the bios of my box to boot from the first hard drive I only get the option to boot from the windows partition or Ubuntu the second hard drive does not appear on grub at all. If I boot in the BIOS from the second drive I can boot from
Kubuntu next there is an option to boot from Vista and then Ubuntu but both of these do not work grub comes up with an error saying cant mount partition and at the bottom of the grub screen is an option to boot from Windows this boots up the ntfs partition located on Hd0 the first drive. I would like to be able to boot from any  of the four installed OS's via grub.
If anybody can help me with his I would appreciate it. as I am new to linux and ubuntu.

Many Thanks Al-Man

---

### Post by stlsaint on 2009-09-15
please post menu.lst. How did you install all the OS...meaning what order and or precdure...step-by-step please! you seem to have to edit your menu.lst to add your other hdd(not the master)!!

---

