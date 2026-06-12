---
title: "Encrypted LVM and boot problem"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by m3w2 on 2009-10-29
Hi,

I recently installed Ubuntu 9.04 AMD64 with the guided encrypted LVM option from the alternate CD. When I rebooted the computer all I got was "**Operating system not found**". To start Ubuntu i have to boot from the Ubuntu-CD and chose "Boot from first hard disk", GRUB loads, I enter passphrase and from there everyting works out fine.

I had the exactly same problem earlier when I was running Fedora 10 on the computer. I'm a Linux-newbie so with the help of Google and a little luck I somehow managed to fix the problem that time, but I can't remember how. I'm not the first one to encounter this problem on this computer model (Fujitsu Siemens Si3655). In *[this thread]("http://ubuntuforums.org/showthread.php?t=1004456")* it says that "**sudo grub-install /dev/sda1**" should fix the issue, so  I tried. Now i didn't need a boot-cd, but instead the boot froze just before i was supposed to enter the passphrase to decrypt the system. After one hour of searching solutions i reinstalled the system again with the same options and the problem remains.

So my question is how do i install the bootloader the right way? As I said I'm a linux-newbie, but I'll attach some system info that may help:

```
m3w2@si3655:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00097098

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38882   312319633+  83  Linux
/dev/sda2           38883       38913      249007+   5  Extended
/dev/sda5           38883       38913      248976   83  Linux
``````
m3w2@si3655:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "si3655" using metadata type lvm2
``````
m3w2@si3655:~$ sudo lvs
  LV     VG     Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  root   si3655 -wi-ao 268.36G                                      
  swap_1 si3655 -wi-ao  11.03G
```

---

### Post by apterix on 2009-10-29
the similiar problem:
[http://ubuntuforums.org/showthread.php?p=8192651#post8192651](http://ubuntuforums.org/showthread.php?p=8192651#post8192651)

Probably your solution is:
[http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)

---

### Post by m3w2 on 2009-10-29
Thanks for your answer, but it's not the same problem. I can get into the system and access my files.

I wonder how to get the computer to boot from the HDD directly, so I don't need a boot-cd.

---

### Post by m3w2 on 2009-11-01
Problem solved! :D

A friend helped me out and was the solution:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0) (hd0,4)
```And then i installed gparted and changed the boot flag to sda5 (mount point: /boot). Now grub loads and I don't need a boot-disk.

---

