---
title: "Problem with USB startup disk creator."
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by Jeff A. on 2009-01-14
I'm new to linux and just installed ubuntu 8.10 on my dell studio and got all the updates.  I'm trying to make a USB startup disk so i can install linux on a lenovo laptop that has no CD drive.

when i open the "create a USB startup disk" option under administration, i have my ubuntu disk in the cd drive and my 2gb cruzer plugged in.  when i start it, it hangs on "starting up."  it never copies any files or anything else.  is there something im doing wrong?

PS - its hard to type this also, cursor jumps around :???:

---

### Post by kranny on 2009-01-14
I would first suggest formating the flash drive in FAT32 and then use 'Create a USB startup disk'

---

### Post by Jeff A. on 2009-01-14
under properties, it says the disk is formatted in "vfat (FAT32)" 

is this correct?

---

### Post by kranny on 2009-01-14
Yes its already formatted As fat32..The issue has bean reported by many people..It may be due to lack of support for all thunb drives...Betwen try to format the cruzer under windows Xp and use unetbootin first and then delete the files and then use it to creat a usb disk under ubuntu

---

