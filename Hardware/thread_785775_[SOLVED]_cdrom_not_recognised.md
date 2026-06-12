---
title: "[SOLVED] cdrom not recognised"
date: 2008-05-07
forum: Hardware
---

### Post by corruptor1972 on 2008-05-07
Hi,

Having online-upgraded my Kubuntu from 7.10 to 8.04, the CD/DVD Writer is not recognised.  There's no node for it in /dev and attempting to mount it using the details in /etc/fstab doesn't work either.

The CD/DVD Writer is an Optorite and it's jumpered as the Slave on IDE1.  It works well in Windows XP and I can boot from my Kubuntu 7.10 CD using it, bit not from an 8.04 CD:  Instead that drops out the Busybox terminal prompt, shortly after making a selection from the menu & drawing the usplash screen.

Here's some more info which I hope can help someone resolve this problem:  The outputs from 'dmesg', 'fstab', 'lshw -C disk' and 'lspci'.

Update:
casper.log in the Busybox session helpfully says:
  *Unable to find a medium containing a live file system*

I have tried disconnecting all USB devices, disabling USB and RAID in BIOS and amending the Grub prompt to disable acpi/apic and to use the irqpoll parameter.  However these efforts have failed.


Does anyone have any idea why this has happened and how to get the drive recognised?


Thanks in advance!

---

### Post by sideburns on 2008-05-07
I don't think it's just Kubuntu, either.  I do support for my sister's Ubuntu box, and it's not recognizing that there's media in either her CD or CD/DVD drive since she did an on-line upgrade to Hardy Heron.  Don't know if it's a bug, or if the upgrade b0rked somethng, but it's another data point.

---

### Post by corruptor1972 on 2008-05-08
\\:D/  SOLVED

Not working setup was as follows:

IDE1 M - HDD
IDE1 S - CD/DVD RW
IDE2 M - HDD
IDE2 S - empty


Now it works like this:

IDE1 M - HDD
IDE1 S - empty
IDE2 M - CD/DVD RW
IDE2 S - empty


So it would appear that 8.04 likes my CD/DVD as a Master device and not as a Slave.  The CD/DVD is now picked up on the Live CD and in the Installed Kubuntu.

:beer:

---

### Post by dougie173 on 2009-02-07
Thanks, This has been confusing me as to why my Mythbuntu box wouldn't play DVDs.

Changed the jumper from Slave to Master et voila. It all works and now I have a happy girlfriend

---

