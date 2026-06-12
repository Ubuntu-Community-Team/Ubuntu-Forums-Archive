---
title: "dual boot xandros - ubuntu remix 9.10"
date: 2009-11-04
forum: Hardware
---

### Post by menuetto on 2009-11-04
I've a problem with a SD card with Ubuntu Remix 9.10.

Thanks to a USB Key with Puppy Linux I've changed the menu.list both in sda1 and sda2 adding:
```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 9.10 Remix, Linux 2.6.31-14-generic (on /dev/sdc1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=d8e1a3fa-5062-4910-85aa-2b28f538f38d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
savedefault
boot
```This option is ok for the booting in my first computer, but it's not right for the Eeepc 701: at the start I press F9, choose for the "Ubuntu 9.10 Remix" and it says something like:
```
err 2: bad file or directory file.
```suggestions?

```
sudo fdisk -l
```gives me the SD Card as sdb1.

---

