---
title: "automount usb partitions to the same mountpoint"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by kappa01 on 2006-08-15
I have several USB devices attached to a laptop running 6.06.  One of these is a hard drive with 3 partitions.  When I first set up the system the drive the paritions come up at /media/sdb1, /media/sdb2, or /media/sdb3.  However, if other devices are attached at boot time, other devices may show up at sdb and this device can get assigned to sdc or another location.

Since I need to use this drive for backups, but my script needs to point to a fixed location and to solve the moving mount point problem, I created /etc/fstab entries for the drive.  But now if when I boot the machine with the drive attached after having booted it with the drive not attached, the partitions aren't mounted and I have to manually mount them.

How can I either get udev to assign the drive to a fixed mountpoint no matter what else is attached or alternatively automount from /etc/fstab whenever the device is attached?

Paul

---

### Post by jordilin on 2006-08-15
The answer is in the following howto:
[http://ubuntuforums.org/showthread.php?t=91948](http://ubuntuforums.org/showthread.php?t=91948)
You can take a look at the following page as well:
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

