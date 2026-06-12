---
title: "liveusb to full installed"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by hallve_revera on 2009-01-07
:confused:
hi.....
have a question here...
is there anyway to FULL install kubuntu 8.04 or 8.10 into usb hdd??

or is there anyway to make liveusb persistence kubuntu 8.10 behave like full installed kubuntu 8.10

---

### Post by lemming465 on 2009-01-10
> is there anyway to FULL install kubuntu 8.04 or 8.10 into usb hdd?
When you get to the disk partitioning stage use the manual option, and put all the partitions such as root and swap on the USB drive.  The install should run normally.

The tricky part is the boot strategy, and that rather depends on what else you have on any internal disks.  If your BIOS lets you pick which disk boots, then when it gets to the boot loader stage pick "advanced", and put grub on the USB drive.  Otherwise, write back with a description of what other OS's are around, how they currently boot, and how you'd like them to boot.  Output from **sudo fdisk -lu** would help a lot. 

If you just go with the boot loader defaults, the MBR on the internal disk will be modified to point at the /boot directory on the external USB, and you won't be able to boot the main hard drive if the USB disk is turned off or unplugged.

> is there anyway to make liveusb persistence kubuntu 8.10 behave like full installed kubuntu 8.10
I don't think so.  If I understand what the liveusb persistence does (and I could be wrong), it's using a copy of the live CD ISO image loopback mounted off the USB drive.  This is not a writeable object the way an ext3 root filesystem would be - that's the point of running an install.

---

### Post by hallve_revera on 2009-01-14
what about software...
do we can install program in the live usb just like the way we install in full installed kubuntu..
is there any program that can't installed to live usb but we can install to full installed kubuntu ????

---

