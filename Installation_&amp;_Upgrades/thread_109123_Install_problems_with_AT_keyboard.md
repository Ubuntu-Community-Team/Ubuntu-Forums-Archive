---
title: "Install problems with AT keyboard"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by tinsami1 on 2005-12-27
I'm trying to install Ubuntu to a 486 PC with 32MB RAM.  The problem is that at boot time the keyboard is not being recognized by Ubuntu, hence I cannot really do anything.  I've tried Warty, Hoary and Breezy - same results.

I've installed Slackware, Debian and Trustix on this machine without such problem.  It's only in Ubuntu.

Is there a boot parameter to force the kernel to initialize/activate AT keyboard support?

---

### Post by sciurus on 2005-12-27
I'm pretty sure a barebones Ubuntu server install uses more than 32mb of RAM, so it sounds like you're asking for pain even if you get this working. I've had good experiences with the 0.6 versions of [Deli Linux]("http://www.delilinux.de/") on that amount of memory.

---

### Post by tinsami1 on 2005-12-28
Ubuntu already has the prepared packages for what I need without the need for recompiling things such as the kernel.

Upon further looking at the logs:  I'm getting this error:

i8042.c: Can't write CTR while closing KBD


My current setup:

HW: 486DX4, 32MB RAM, 1.2GB HD, CD-ROM drive

I have Debian Sarge (core-only) installed in it.  The BIOS is so old, it does not support booting off the CD drive, so I copied the vmlinuz and initrd.gs files  from the install dir in the CD to a folder under /boot.  I then made a new entry in GRUB ("Ubuntu Install CD") for this pair.  Then I rebooted.

The keyboard works while in GRUB.  When I choose the Ubuntu Install CD entry and loads Ubuntu's vmlinuz, the keyboard doesn't work anymore.

---

