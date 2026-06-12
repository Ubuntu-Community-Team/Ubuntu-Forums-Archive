---
title: "help understanding some grub and fdisk output"
date: 2008-12-02
forum: General Help
---

### Post by NewbuntuUser777 on 2008-12-02
Hi,

I'm very new to unbuntu so forgive me if this is a rtfm kinda thing.

I'm curious how to interpret the following grub output.  Specifically, is it saying that I have two seperate installations of ubuntu (2.6.27-9 and 2.6.27-7)?

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		243f2050-8624-446d-bee9-454f52eb21b9
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=243f2050-8624-446d-bee9-454f52eb21b9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		243f2050-8624-446d-bee9-454f52eb21b9
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=243f2050-8624-446d-bee9-454f52eb21b9 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		243f2050-8624-446d-bee9-454f52eb21b9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=243f2050-8624-446d-bee9-454f52eb21b9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		243f2050-8624-446d-bee9-454f52eb21b9
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=243f2050-8624-446d-bee9-454f52eb21b9 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		243f2050-8624-446d-bee9-454f52eb21b9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


Also have a question about the partition called 'extended' below.  Is that part of ubuntu?

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17124   137548498+   7  HPFS/NTFS
/dev/sda2           37760       38914     9268224    7  HPFS/NTFS
/dev/sda3           17125       37759   165750637+   5  Extended
/dev/sda5           17125       37007   159710166   83  Linux
/dev/sda6           37008       37759     6040408+  82  Linux swap / Solaris

Partition table entries are not in disk order


Again sorry if these should be obvious from the docs.
Charles

---

### Post by cdtech on 2008-12-02
If you really want to know the forensics of the GRUB boot menu:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI](http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI)
As for the extended partition:
[http://www.linfo.org/extended_partition.html](http://www.linfo.org/extended_partition.html)

---

### Post by NewbuntuUser777 on 2008-12-02
I guess my question is more specific but thanks for the grub page; lots of good information.


I now get two options upon booting, I can load ubuntu kernel 2.6.27-9-generic, or
ubuntu kernel 2.6.27-7-generic (ok three options if you count vista).  

I don't recall installing multiple kernals and I'm not sure why there are two or what the significance of that is.  Is this typical behavior or could it indicate an installation problem or a possible security issue?

---

### Post by NewbuntuUser777 on 2008-12-02
I was able to figure it out.

When a new kernal is installed the older one is kept in the event the user is unable to boot into the new one.

ubuntuforums.org/archive/index.php/t-949158.html

---

