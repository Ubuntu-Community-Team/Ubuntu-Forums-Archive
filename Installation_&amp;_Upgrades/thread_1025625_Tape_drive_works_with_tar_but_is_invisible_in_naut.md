---
title: "Tape drive works with tar but is invisible in nautilus"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Jan Sloep on 2008-12-30
Hi all,

I have Ubuntu 8.10 (64 bit) and a (scsi) ADR50 Onstream tape drive. The system recognizes the tape drive and I can use the "mt" and "tar" commands on it. This works all fine. 

Now I want to use the drive with "grsync" but I can not connect to the tape drive as it is not visible, also not in Nautilus. 
If I try to mount /dev/st0 it says that dev/st0 can't be found in /etc/fstab or /etc/mtab. 

Can somebody tell me how I can connect to the tape drive from grsync and nautilus or what I am doing wrong

P.S. I am new in Linux.

---

### Post by lemming465 on 2009-01-01
I don't think you are going to be able to use tools other than "tar", "star", "dd" or specially written backup programs with a tape drive.  Tapes drives are *character mode* devices, not *block mode* like disks, and stuff like nautilus and rsync or grsync just won't understand them.  You can't just open them and seek around; at a low level it's all wacky ioctl's specific to the tape drive and controller.

---

