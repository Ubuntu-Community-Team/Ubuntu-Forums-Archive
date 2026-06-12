---
title: "FreeBSD/ubuntu dual boott problem"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by epiphiny on 2007-05-22
Hi there, I've been messing around with dual-booting between Windows XP and Ubuntu 7.04 for ages now, and thought that it was a bit of a change, and decided to install FreeBSD to give that a go. As I didn't want to loose data, I removed my second hdd (SATA btw), and installed FreeBSD on a spare partition on my first hard drive, next to windows. However, when I popped my second hard drive back in the computer, all I got after all the BIOS POST stuff was a non-flashing cursor at the top of the screen; no grub or anything.

To try and make things clear, my partitioing was;

SATA Drive 1;

sda1: Windows XP
sda2: FreeBSD

SATA Drive 2;

sdb1; Ubuntu 7.04
sdb2; Swap
sdb3; Grub partition (my BIOS was set to boot from this hdd).

Ok, I'm also seeing in my BIOS three entrries in under 'boot hard drive', both for my SATA drive 2. How can this be?

Any advice would be really appreciated, thanks in advance,
James

UDPATE:

Ok, so I've now tried completely wiping sda, using a grml livecd, and running;

dd if=/dev/zero of=/dev/sda

This doesn't cure the problem, however; I'm still seeing just a cursor at boot after POST.

---

### Post by Tilo on 2007-05-31
I'm not sure about FreeBSD, but I'm using OpenBSD a lot - and it does not use the same
partitioning (disk label) format as Windows or LINUX.. that's probably the problem

---

### Post by epiphiny on 2007-05-31
Hi all,

Well the problem, whatever it was, has now been fixed.

Even though I had re-flashed my motherboards BIOS, and reset the CMOS memory, running a 'reset to factory defaults' after the reset seemes to have cleared up whatever the problem is.

I may post back in this thread if I work up the courage to try installing FreeBSD again, however its gone at the moment as I deleted the drive using 

```
dd if=/dev/null of=/dev/sda
```

from a knoppix boot cd.

---

### Post by Tilo on 2007-05-31
well, yes - what that does is to  zap-out the partition table (first block of the device) 
but it will also delete all your data..

btw. this would have been sufficient:

  dd if=/dev/null of=/dev/sda bs=512 count=1

 Maybe the better way to do this FreeBSD installation is to use VMware or something similar 
and to install FreeBSD as a virtual machine - so you don't let it touch your actual boot-block
and partition table

---

### Post by epiphiny on 2007-05-31
Fortuantely I didn't have any unrecoverable data on that drive, as I had taken the precuation of backing up my windows partition with partimage.

I'm interested to know, however, how you got openBSD installed; was it before or after installing linux?  If it was after, did you encounter any booting /bootloader problems?
Many thanks

---

### Post by Tilo on 2007-05-31
I use OpenBSD for my firewall - not in conjunction with any other OS - just all by itself :)

   T.

---

