---
title: "Installation Problems - vfat , error 18, &amp; error 22!"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by evyxmsj on 2009-06-06
Hello everyone,

I realise that there have been innumerable posts on this subject, but I find myself turning in circles. I'd really appreciate it if someone could address my problem specifically...especially as I am a complete novice when it comes to Linux/Ubuntu. So:

_What I want to do_

I want to use an *external *(USB) freecom hard drive as a portable OS. I would like to perform a full installation of the latest Ubuntu version onto the hard drive. *So this is not dual booting*.

Preferably, I would like to create a partition on the drive with FAT32 formatting, in order to allow simple transfer of data.

_What I have_

- My main computer is an Advent 4211 netbook that can boot from USB.
- Freecom HDD (I can get the full info if needed).
- Ubuntu Live CD

[U]What I've tried
[/U]
**First Attempt:** My netbook doesn't have a cd drive, so the simplest option for me was to aquisition a friend's computer and disconnect the internal SATA hard drive. I then booted from the CD, with the USB hard drive plugged in. I followed the Ubuntu install wizard with manual partitioning:
 - primary partition "/" ext4 - 30 GB
 - logical partition swap - 3 MB
 - primary partition "/store" FAT32 - 217 GB
 - Boot loader set to sd0 (or hd0, I can't remember)

*Result:* failure to create vfat partition. At this point I figured I'd skip the FAT32 idea, and stick with ext4 (I also tried ext3). It seems I can create a vfat partition later within ubuntu.

**Second attempt:** I started again with the above options, but changed the partition "/store" to ext4.

*Result:* installation finished, but restart resulted in Grub error 18. 

A little research led me to believe that it might be a problem with BIOS. Suggested options included changing BIOS hard disk options from LBA or Auto, to Normal. For some reason, I don't have this option (and does it even apply to USB drives?). So I followed another suggestion: I created a seperate, smaller partition for booting:

**Third attempt: **
 - primary partition "/boot" ext4 - 5 MB
 - primary partition "/" ext4 - 30 GB  
 - logical partition swap - 3 MB
 - primary partition "/store" ext4 - 212 GB
 - Boot loader set to sd0,0 (ie the /boot partition, not sd0)

I must admit that the last setting was just a guess as I couldn't find any advice.

*Result: *installation finished, but the restart resulted in Grub error 22.


I am at my wits' end! Can anyone help me? Please bear in mind that I am a complete beginner when it comes to linux.

---

### Post by evyxmsj on 2009-06-06
Well, after considering my first post, I thought: "screw it, I'm gonna try the 'use entire disk' option".

I also left the boot loader option on the default, hd0.

No luck - now I get error 2.

Trying to install Ubuntu on an external USB drive has well and truly defeated me!

EDIT: Hard drive is a Freecom branded SAMSUNG HM250JI (250 GB, 5400rpm)

---

