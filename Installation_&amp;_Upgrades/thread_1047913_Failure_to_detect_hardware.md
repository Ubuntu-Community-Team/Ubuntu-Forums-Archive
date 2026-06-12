---
title: "Failure to detect hardware"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by Dark_Helmet on 2009-01-22
I've tried many things, but cannot get an Ubuntu install going on an older machine. I'm left thinking that I need to find drivers and integrate them into the boot-install process, but need guidance. Here's what I've tried:

1) Regular CD install (8.10 desktop and server)
2) SmartBootManager ([https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager))
3) Install with floppies ([https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies))
4) debootstrap (while running under Knoppix)
5) unetbootin ([https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows))
6) install on another machine, transfer hard drive back

Every attempt has failed. The primary problem is this: neither my CD drive nor my network card are detected. All of the methods above (except 6) seems to only get the machine to the hardware detection--which fails for me.

I have (old): Tyan Tiger motherboard, HP DVD writer 100i, and 3com 3c905b network card.

However, Gnoppix 1.0 and Knoppix live CDs boot completely. They detect properly. So I know the hardware works. The problem is Ubuntu's detection.

Under the install-by-floppy method, I tried the alternate driver disks. However, the 3c905b driver was not included and non of the other 3com drivers worked. The cdrom driver disk did not work, but I have not had time to retry that.

So, given the above, how in the world do I (1) acquire a 3c905b driver that will work with the installer or (2) acquire a CD driver (probably a full-fledged IDE driver) that will work with the installer. And the followup: how to incorporate it into the install process (reburn CD iso, driver disk, or whatever)

---

### Post by Dark_Helmet on 2009-01-23
I finally installed 8.10.

I downloaded the 8.04-alternate CD image, and that installation worked fine. From inside the 8.04 system, I used the update manager to upgrade to 8.10.

---

