---
title: "HP EliteBook 6930P"
date: 2015-04-29
forum: Hardware
---

### Post by Lee_Henderson on 2015-04-29
Hello, can anybody please help?  This laptop currently has Windows 8 and its a dog with it.  Im trying to install Ubuntu 15.0.4.  It boots from the DVD, sees the video/network/wifi/sound all fine.  You can even see the current internal HDD pop up.  Try to install and it cannot see the hard drive, not even listed.  Ive tried changing the HD controller mode and nothing works.  Can anybody please help?[ATTACH=CONFIG]261642[/ATTACH]

---

### Post by coffeecat on 2015-04-29
This sounds like an odd question when you say you are using a laptop, but has the hard drive ever been used in a RAID? You see this problem when there is RAID metadata left on the drive.

---

### Post by Lee_Henderson on 2015-04-29
Its a HP laptop yes, when booted from the Ubuntu DVD i run the command to see if its ever been a RAID and it says no.  Ive tried IDE AHCI and RAID modes in the BIOS and it makes no difference.  It boots up in Windows 8 in IDE mode fine

---

### Post by Lee_Henderson on 2015-04-29
But I open GParted from the Live CD and it sees the HD and lets me format it.  But it wont install the OS onto it

---

