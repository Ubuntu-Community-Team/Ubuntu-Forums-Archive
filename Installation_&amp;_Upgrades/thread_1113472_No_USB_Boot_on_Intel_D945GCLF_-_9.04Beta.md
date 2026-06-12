---
title: "No USB Boot on Intel D945GCLF - 9.04Beta"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by ve7mdl on 2009-04-01
Hello All,

I managed to pick up an inexpensive Intel motherboard (D945GCLF) with a 1.6 GHz Atom processor and added 2GB of memory and a 32 GB SSD.  I want to run Ubuntu 9.04 (Beta) on it, but I can't get a USB stick to boot.  The USB stick is created with the desktop ISO image using "Create USB Startup Disk" in Ubuntu 8.10 on another machine.

When trying to boot, the BIOS simply says "Boot Error".

Yet, when I created a USB startup of Netbook Remix (9.10 Alpha) it booted fine.  What is the difference in the boot sequence?

BTW, I previously had Ubuntu 8.10 running on the machine, which I loaded from a CD, but it a real pain to take the small box apart and connect the CD drive, so I prefer to boot from the USB stick, if possible.

I did try disabling the LAN support in the BIOS, BTW.

Update: I created a new 9.04 Netbook-Remix USB stick and it boots fine on the system.  I then deleted all the files and copied the files from a 9.04 Desktop USB drive.  Still no boot.

Any other suggestions?

Cheers,                ....Erik.

---

### Post by TimMedcalf on 2009-12-13
Just came across this same problem - found that changing the usb setting in the bios to "All Fixed" resolved the issue.

Better late than never!

---

