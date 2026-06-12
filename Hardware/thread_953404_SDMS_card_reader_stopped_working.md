---
title: "SD/MS card reader stopped working"
date: 2008-10-20
forum: Hardware
---

### Post by Neftronics on 2008-10-20
Hi,
my SD card reader suddenly stopped working on my Acer laptop. When I boot into Windows it does work. I am using a 2GB card which auto-mounted no problem. Now it is no longer visible even in Gparted.
A Dmesg shows this:
> ~$ dmesg | grep mmc1
[   31.405521] mmc1: SDHCI at 0xd2003100 irq 17 PIO
[   31.802634] mmc1: unrecognised SCR structure version 1
[   31.802648] mmc1: error -22 whilst initialising SD card
[  194.701131] mmc1: new SD card at address 0001
[  195.017028] mmcblk0: mmc1:0001 064MB 1014528KiB 
[  238.727474] mmc1: card 0001 removed


This seems to be a common problem, but, if I insert a 1GB card, it automounts and works fully. I could understand if the reader was not capable of going over 1GB, but it *did* work with 2GB cards!
I also tried reformatting it to FAT32 in Windows, but still no joy.

Any help would be appreciated. I am a noob!

Release 8.04 (Hardy)
Kernel 2.6.24-19-Generic
Gnome 2.22.3

---

### Post by cairnzi on 2008-10-20
im sure fat 32 is a windows? try formating it in ubuntu and see if it works then, not sure if it will work but it did when i had problems with my toshiba lappie:)

---

