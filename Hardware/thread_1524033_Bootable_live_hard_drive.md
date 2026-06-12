---
title: "Bootable live hard drive"
date: 2010-07-04
forum: Hardware
---

### Post by as2000 on 2010-07-04
Is it possible to make a old 2.5GB hard disk similar to a usb bootable/cd disk to install Ubuntu? I would like to utilize an old hard drive to do this since it would work a lot faster than installing from a cd/usb. Any idea how to accomplish this?

---

### Post by C.S.Cameron on 2010-07-04
Just yesterday I cloned a 2GB persistent, (disk image), flash drive over to an old 8GB HDD booting from the Live CD using:
```
sudo dd if=/dev/sdb of=/dev/sda
```
Where sda was the HDD and sdb was the Live USB.
It worked fine.
I then used gparted to expand sda1 to fill the disk.
If you try this you should probably start with a 2GB flash drive.

Above assumes that the 2.5GB is the only internal HDD. Confirm device names before proceeding.

---

### Post by gordintoronto on 2010-07-04
There are several ways to do this. The simple way is to open up your computer and install the old hard drive in place of the current hard drive. Easier said than done if the old drive is IDE and the current one is SATA.

For less than $20 you can buy an adapter to make an old hard drive an external USB drive. Once again, pay attention to the IDE/SATA question. (A 2.5 GB drive is almost certainly an IDE drive.)

The previous poster told you a good way to get Ubuntu onto the external drive. Installing to an external drive has a few pitfalls; it's easy to mess up whatever is installed on the internal hard drive.

---

### Post by -kg- on 2010-07-05
> **as2000 said:**
> Is it possible to make a old 2.5GB hard disk similar to a usb bootable/cd disk to install Ubuntu? I would like to utilize an old hard drive to do this since it would work a lot faster than installing from a cd/usb. Any idea how to accomplish this?

 You want to make the old HD operate as a "Live CD"/Installation CD?  I would think that Unetbootin would do the job.  Just install it from the repos (10.04...I don't know if it's available in the repos for earlier versions) and you can make it a Live/Installation CD for almost any distro out there, whether they're in the default list or from a downloaded .iso.

Unetbootin will do what it does no matter what kind of media you're using.

---

### Post by C.S.Cameron on 2010-07-05
Both UNetbootin and usb-creator appear to only install to USB drives, 
It may work to put the HDD into an external USB enclosure and then use a Live installer.
I know it works to clone the Live installation from USB drive to HDD.

---

