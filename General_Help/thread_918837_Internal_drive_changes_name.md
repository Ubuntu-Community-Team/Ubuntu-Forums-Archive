---
title: "Internal drive changes name"
date: 2008-09-13
forum: General Help
---

### Post by jefuchs on 2008-09-13
I have a secondary drive for storage, and use my primary only for the operating system.  The secondary drive is named "/media/disk" by default when Ubuntu boots.

Problem is, when I boot my computer with any USB storage device attached, the device gets named /media/disk, and the hard drive becomes /media/disk-1, or similar.

This causes problems, because programs look for files in /media/disk, and can't find them.  I use the extra drive as a shared drive for VirtualBox, and VB won't boot another OS at all if the shared folder isn't found.

I solve this by removing the USB device and re-booting, but there has to be a better answer.  Why can't the drive be called the more accurate /dev/sdb1?  Can I make Ubuntu give the drive a name that sticks?

---

### Post by chrisccoulson on 2008-09-13
Using the device node (/dev/xxxx) won't make the name any more persistent either, because the device node will likely also be different when you boot with the USB drive connected.

If you want a persistent name, then either specify a mount point for the internal disk in your /etc/fstab or give your disks a volume name. This will then become the name of the mount point when the volume is auto-mounted. The steps for naming a volume can be found at [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

