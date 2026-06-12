---
title: "Ubuntu 9.04 on a flash drive?"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by rfoxtail on 2009-06-18
Hi, I'm using Ubuntu 9.04 Live off a CD, and I'd like to haveUbuntu on a flash drive. I use the USB Startup Disk Creator, but it only creates a copy of the CD on my disk. I'd like to have it retain my own data like accounts or settings while on my flash drive, is this possible?

Sorry if this has been answered already or is obvious to anyone but me.

---

### Post by 123456789123456789123456 on 2009-06-18
I know that you can create a bootable flash drive, bassically a clone of the live cd on the flash drive, rather or not the live cd on flash is able to read/write to the disk, I don't know, it all depends on rather it consideres the flahs drive write protected or not.  You either have to have a working windows machine, a live cd, and a certian program for windows to create the drive, you can do it command line thorugh ubuntu, but I understand you have to have it installed on the hard disk, and you need to have a live cd, or live cd iso file on the disk somewhere.  Search google for booting Ubuntu off of flash.

---

### Post by raymondh on 2009-06-18
You may need a "persistent" flash drive.  

Granted this is for 8.10.

[http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Good luck.

---

### Post by Mighty_Joe on 2009-06-19
The USB Startup Disk Creator can create a "persistent" USB Live CD which will preserve your changes ([see here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")).
Personally, I just installed Ubuntu directly to the USB flash drive. The full install is faster than the Live CD install, but it takes up more space (2Gb vs. 700Mb). Flash memory can wear out, and USB is pretty slow, but you can take some steps to mitigate those concerns.  I used this [install]("http://beastie.cs.ua.edu/cs150/usb-install.html") and [configure]("http://beastie.cs.ua.edu/cs150/configuration.html") guide to set my flash drive up.  Works great.
Store your important files elsewhere (I use a NAS)!

---

