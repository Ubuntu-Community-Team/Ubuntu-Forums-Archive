---
title: "Confused why my grub is not working properly"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by wolfe on 2009-03-20
I just did a fresh install of both windows and ubuntu on my new computer.  I thought I did the right thing by installing Windows first, and then Ubuntu.

I know there is some mixup over which device is #1, but I have the bios set to boot from my 150gig drive.  Thats where grub is located I believe.  Ubuntu boots without fail, but I get the dreaded NTLDR missing when I try to load windows.  I would really like to learn how to fix this instead of doing a windows repair and blowing away grub.

I am attaching my menu.lst and the output of fdisk -l

I hope someone can make sense of what is wrong here, thanks in advance guys!

fdisk -l
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cd9a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001   83  Linux

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99ae05e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6502    52224448+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2            6503       18241    94293517+   5  Extended
/dev/sdb5            6503        6623      971901   82  Linux swap / Solaris
/dev/sdb6            6624       18241    93321553+  83  Linux

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002d514

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       12749   102406311    7  HPFS/NTFS
/dev/sdc2           12750       36481   190627290    5  Extended
/dev/sdc5           12750       36481   190627258+  83  Linux
```

menu.lst
```
title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		12893ea2-e8cb-4d80-83de-8033f74d8c53
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=12893ea2-e8cb-4d80-83de-8033f74d8c53 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		12893ea2-e8cb-4d80-83de-8033f74d8c53
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=12893ea2-e8cb-4d80-83de-8033f74d8c53 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-9-generic
uuid		12893ea2-e8cb-4d80-83de-8033f74d8c53
kernel		/boot/vmlinuz-2.6.28-9-generic root=UUID=12893ea2-e8cb-4d80-83de-8033f74d8c53 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-9-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-9-generic (recovery mode)
uuid		12893ea2-e8cb-4d80-83de-8033f74d8c53
kernel		/boot/vmlinuz-2.6.28-9-generic root=UUID=12893ea2-e8cb-4d80-83de-8033f74d8c53 ro  single
initrd		/boot/initrd.img-2.6.28-9-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		12893ea2-e8cb-4d80-83de-8033f74d8c53
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Professional x64 Edition
rootnoverify	(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by dstew on 2009-03-20
At first glance it looks like it is set up properly to boot Windows on /dev/sdb1. However, sometimes the BIOS will re-number the disks when you change the boot order. It is possible that the 150 Gb disk is actually disk 0 in your BIOS when it boots. If that is the case, you might try changing the Windows root entry to```
rootnoverify (hd0,0)
```and getting rid of  the map statements. You can try this by editing the menu.lst file, or by entering 'e' when the grub menu comes up. If you use the 'e' method, and it works, you will have to make the change permanent by editing the menu.lst file later, because the changes you make with 'e' are only temporary.

---

### Post by meierfra. on 2009-03-20
Edit: I hadn't seen dstew post, when I posted this. Follow dstew's advice first.



Open menu.lst via 

```
gksudo gedit /boot/grub/menu.lst
```

Add the following to the end of file

title		Windows XP Professional x64 Edition (hd0)
rootnoverify	(hd0,0)
chainloader	+1

title		Windows XP Professional x64 Edition (hd2)
rootnoverify	(hd2,0)
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


Reboot and try both entries. (The first entry should work if XP is on the 150GB drive you are booting from, otherwise the other one. In any case try both)

If one of them works, you can deleted the other entrees  from menu.lst.
If none of them work, report all error messages you got.

---

### Post by wolfe on 2009-03-20
Thanks guys.  dstew's advice resolved it for me.  yay, now I can get back to overclocking this beast.

---

