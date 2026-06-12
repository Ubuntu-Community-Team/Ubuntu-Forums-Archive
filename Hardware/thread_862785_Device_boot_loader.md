---
title: "Device boot loader?"
date: 2008-07-17
forum: Hardware
---

### Post by fk4rp6 on 2008-07-17
Anyone know of a boot loader that can be used on a floppy or CD, that can be used to boot from a hard drive controller?

I have an older machine in which the BIOS does not support booting from an add-on card.

I am able to install an OS on the HDD using the hard driver controller. But then not able to boot the OS.

---

### Post by logos34 on 2008-07-17
Interesting predicament.  Too bad I can't think of a solution.  Maybe there's a Bios upgrade that adds that feature (a long shot, and you've probably already checked).  

You might try [Smart Boot Manager]("http://sourceforge.net/projects/btmgr/") floppy -- it can boot cdrom drives when the Bios does not support it, so maybe it can see and boot the HDD on the controller card

---

### Post by fk4rp6 on 2008-07-18
I haven't checked for BIOS updates.  Simply because the system is so old I would be surprised if a BIOS update would add the functionality.

I'll do some looking today for a BIOS update just to make sure.  And certainly check out the boot loader you mentioned.  I'll be trying that at out soon as I get home from work today :)

Thanks for the post.

---

### Post by phidia on 2008-07-18
[This]("http://www.xs4all.nl/~lennartb/bootloaders/node3.html") and [this]("https://wiki.ubuntu.com/Booting") could be useful.
From the 2nd link: > Finding the boot loader

For older computers (old BIOS) the boot loader must be on the first hard drive or a floppy. Some BIOSes gives a selection between different hard drives and even USB drives. Most computers can also boot from a CD.

When the boot loader is split in two, like grub, the first part has to find the second part! Some intelligence can be built into the first part, but in general it has to use BIOS calls to find the second part (see grub section below).
 Grub can be installed to a floppy also, but that may not help you in this case.

---

### Post by logos34 on 2008-07-18
yeah, like phidia said there is also the option of a grub boot floppy.  Here's how you make it:
[https://wiki.ubuntu.com/GrubHowto/BootFloppy](https://wiki.ubuntu.com/GrubHowto/BootFloppy)

But I'm not sure if grub will be able to find the drive on the controller card at boot (detecting and installing linux to it from a cd is another matter).

Or else maybe create a separate /boot partition on the main drive.

---

