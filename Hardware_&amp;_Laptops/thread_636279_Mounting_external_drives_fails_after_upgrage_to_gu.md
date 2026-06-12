---
title: "Mounting external drives fails after upgrage to gutsy"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by naurus on 2007-12-09
I have an issue with HAL (i think). Ever since upgrading (through dist-upgrade) from feisty to gutsy I've lost the ability to automatically mount any external drive, be it a USB HD, thumb drive, or camera.  I think the problem lies somewhere within HAL because when I mount any of them with *sudo mount* it works perfectly, except that I have to use *sudo umount* to unmount the drive because using the unmount option in the right click context dialog gives you the error that the device is not in the HAL device list.

The problem is very similar to [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/27689]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/27689"),  but the fix at the bottom doesn't work for me because there is no 'hal' user

This is the error message:
> mount: wrong fs type, bad option, bad superblock on /dev/sdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so.

Thanks,
Naurus

---

### Post by SorryGoFish on 2008-04-08
See: [http://ubuntuforums.org/archive/index.php/t-591012.html](http://ubuntuforums.org/archive/index.php/t-591012.html)
I had the same issue, my fstab was set to assume I have a cdrom drive, which I do not.

---

