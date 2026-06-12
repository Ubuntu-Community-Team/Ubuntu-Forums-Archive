---
title: "How to chainload Vista bootloader through GRUB?"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by Leebria on 2009-09-07
I have 3 hdd's, one with Ubuntu 9.04, one with Windows Vista Ultimate, and the other as a storage drive. I would like to use GRUB as my bootloader, but I am having troubles chainloading Vista. My setup is:
[LIST]
[*]HDD 1 (Ubuntu): /dev/sda
[*]HDD 2 (Storage): /dev/sdb
[*]HDD 3 (Vista): /dev/sdc
[/LIST]

My menu.lst entry is:

title           Windows Vista Ultimate 64-bit
rootnoverify            (hd2,0)
makeactive
chainloader +1

When I attempt to boot off the Vista entry, I get an error saying "BOOTMGR is missing." However, when I change my HDD boot order in BIOS and set the Vista HDD as first, I can successfully boot Vista. Any help is much appreciated. Thanks!

---

### Post by lisati on 2009-09-07
This is what I have on my laptop, which has one physical disk drive, and Vista Home Premium installed:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader, Home Premium)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```
The only difference I can see other than the version of Vista and the pointer to the correct partition is the line "savedefault"

---

### Post by Leebria on 2009-09-07
SOLVED

The error was with rootnoverify (hd2,0), should have been (hd1,0). Thanks for the reply lisati. Please close.

---

