---
title: "Mounting Linux Extra Partition for Home Folder"
date: 2008-06-17
forum: Hardware
---

### Post by brett11808 on 2008-06-17
I would like to use my large Linux Partition to put my Home file on, but I am unsure on how to do that? looking through the forums every one asks for the out puts of sudo fdisk -l so here it is please let me know if you need any other info to help me out thank you all much!
```
brett@brett-laptop:~$ sudo fdisk -l
[sudo] password for brett: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2416    19406488+  83  Linux
/dev/sda2           11978       12161     1477980    5  Extended
/dev/sda3            2417       11977    76798732+  83  Linux
/dev/sda5           11978       12161     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Odrodzona-Sarmacja on 2008-06-18
I would use personally "sudo blkid", but any way you must edit your fstab ["gksudo <name of your text editor here like mousepad, gedit> /etc/fstab"] file and add there line like:
"/dev/sda3 /home ext3 relatime 0 2"
Then run "sudo mount -a" to mount it directly. On reboot it should mount automatically from now on.
Good luck!

---

