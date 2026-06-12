---
title: "mount usb hd for noob"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by dannemil on 2006-10-20
I am having a very hard time using fstab to mount an external usb hard drive on boot. I keep getting  "bad superblock" error. If I plug the drive in while already in gnome and look at dmesg |tail here is what I get:

 dmesg |tail
[17179973.980000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179973.980000] SCSI device sdb: 195371568 512-byte hdwr sectors (100030 MB)
[17179973.980000] sdb: assuming drive cache: write through
[17179973.980000] SCSI device sdb: 195371568 512-byte hdwr sectors (100030 MB)
[17179973.980000] sdb: assuming drive cache: write through
[17179973.980000]  sdb: sdb1 sdb2 < sdb5 >
[17179974.012000] sd 3:0:0:0: Attached scsi disk sdb
[17179974.012000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[17179974.012000] usb-storage: device scan complete

Here is the output of fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11783    94646916   83  Linux
/dev/sda2           11784       12161     3036285    5  Extended
/dev/sda5           11784       12161     3036253+  82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      248976   83  Linux
/dev/sdb2              32       12161    97434225    5  Extended
/dev/sdb5              32       12161    97434193+  8e  Linux LVM

The usb drive is /dev/sdb

Could this have something to do with the fact that I have a part of that drive formatted for a virtual machine using VMWARE?

I also wonder about the line from dmesg |tail that shows < sdb5 > in angle brackets.

By the way, if I use System > Adminisitration > Disks I can mount that drive, but I'd like to be able to do this automatically using fstab.

Jim ](*,)

---

### Post by kidders on 2006-10-20
Hi there,

Thanks for including your log info in your question :-) (Many people don't bother!) Could you post your fstab line though?

**Edit:** I forgot to say that "Bad superblock" means your filesystem is corrupted. The most usual cause of the message is specifying the wrong filesystem type though ... that's why I'm interested in the /etc/fstab line you're using.

---

### Post by dannemil on 2006-10-22
Thanks for the reply. Here is the line from fstab that attempts to mount of the usb drive:

/dev/sdb5        /home/dannemil/mnt/usb     ext3    defaults,errors=remount-ro 0       1

---

### Post by kidders on 2006-10-23
Hey again,

It seems you're trying to mount an LVM partition as though it were an Ext3 filesystem, which will fail. I don't use it myself, so I can't say much more than that, but I'm sure there's plenty of help on LVM on here :-)

---

