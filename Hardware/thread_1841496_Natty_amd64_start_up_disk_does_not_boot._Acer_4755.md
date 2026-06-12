---
title: "Natty amd64 start up disk does not boot. Acer 4755 (i3-2330m)"
date: 2011-09-09
forum: Hardware
---

### Post by staticd on 2011-09-09
Ubuntu 11.04 i386 start up disks boots and installs fine on an Acer 4755 laptop. The 11.04 amd64 usb startup disk and the live CD (both of which have worked fine for other machines) however do not boot on this laptop.

A message is displayed " error: prefix is not set"
followed by the grub menu "try without installing/install/check disk". 
The purple splash does not appear.
Selecting any of the options just leads to a blank screen that stays on indefinitely.


Thanks in advance.

---

### Post by staticd on 2011-09-15
Bump :)

---

### Post by staticd on 2011-09-16
See also: [http://ubuntuforums.org/showthread.php?t=1843130](http://ubuntuforums.org/showthread.php?t=1843130)

Solution that worked for me:

1)Make a x64 10.04 start up disk.
2)If made with >=10.10 startup creator, replace the 
/media/pendrive/syslinux/vesamenu.c32 
with the copy in 
/usr/lib/syslinux/vesamenu.c32
3)delete all the files on the pendrive except those in the syslinux folder.
4)copy all the stuff from the 64bit natty iso except: boot,efi and the isolinux folders to the pendrive.
5)Boot away.... I'm writing this post from the freshly installed and running 64 bit natty.

Basically this roundabout work around uses the 10.04 bootloader to launch the natty files.
step 2 is needed because the new usb creator is broken wrt 10.04.

---

### Post by staticd on 2011-09-16
**Far cleaner and faster Solution:**
1)copy all the stuff from the 64bit natty iso except: boot,efi and the isolinux folders to the empty pendrive.
Use mount -o loop OR archive manager OR archive mounter(comes by default in Ubuntu 11.04)
2)
```

sudo grub-install --boot-directory=/media/pendrive/boot /dev/sdb

```3)copy the iso/boot/grub/grub.cfg to /media/pendrive/boot/grub/grub.cfg

Boot away...

---

### Post by peGGi on 2011-11-28
Hi staticd,

Thanks for posting your solution on the request for help I started ([http://ubuntuforums.org/showthread.php?t=1843130](http://ubuntuforums.org/showthread.php?t=1843130)).

I'm having another go at installing Ubuntu 64-bit.

Can you give me a little more detail on your solution?  I'm a Linux newbie, and currently using Windows, so please keep that in mind!

---

