---
title: "Problem with USB disk, only on boot"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by ShamusPatt on 2006-01-01
Hi. I have an unusual problem with a USB hard drive I have. If I plug it in while the system is running, hotplug works flawlessly; it gets mounted and a File Browser window is opened. However, if it's plugged in when the system boots, I get I/O errors and the boot process eventually stalls after one of them. The I/O errors are like this, appearing after "* Loading Modules" and again after "* Setting up LVM Volume groups" during the boot process:

Buffer I/O error on device sdb, logical block 0

If I unplug the drive, the boot carries on as normal, but it seems I cannot boot the system while it's plugged in.

I'm running "Breezy" with kernel 2.6.12 and all other current updates.

The drive is a USB-powered 80GB drive. It's sold a "ComStar" but the USB identification is " ID 04cf:8818 Myson Century, Inc. Fast 3.5" External Storage".  The drive itself has this identification:

USB Mass Storage support registered.
Vendor: FUJITSU   Model: MHT2080AH         Rev: 006C
Type:   Direct-Access                      ANSI SCSI revision: 00D

Anyone have any idea what is wrong?

---

### Post by Sef on 2006-01-03
It seems that your computer is trying to boot from your USB hard drive.   You go into the boot menu and reset how the computer boots.

---

### Post by ShamusPatt on 2006-01-03
No, I don't think so. The diagnostics I mentioned are from Ubuntu loading (I can see them in "/var/log/kern.log"), so it has definitely booted from my internal hard drive by this point.

The system does seem to be trying to access it, no doubt, but not to boot from.

---

