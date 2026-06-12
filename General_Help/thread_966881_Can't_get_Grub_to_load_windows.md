---
title: "Can't get Grub to load windows"
date: 2008-11-01
forum: General Help
---

### Post by kid_bender2000 on 2008-11-01
This is my Menu.lst:

[COLOR="Blue"]## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a060fb0a-8a11-41dd-88d9-95d1258dcae7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a060fb0a-8a11-41dd-88d9-95d1258dcae7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1[/COLOR]



[COLOR="Black"]This is my output for "fdisk -l":[/COLOR]

[COLOR="Blue"]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef5fef5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26108   209712478+   7  HPFS/NTFS
/dev/sda2           30153       30401     2000092+  82  Linux swap / Solaris
/dev/sda3           26109       30152    32483430   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96c8ee10

   Device Boot      Start         End      Blocks   Id  System
[/COLOR]

Device Map:
(hd0)	/dev/sda
(hd1)	/dev/sdb

When I select the Windows NT/2000/XP option, it tells me NTLDR is missing. I've googled it to no avail

---

### Post by caljohnsmith on 2008-11-01
Since Windows is on the same drive as Grub, you don't need to use Grub's mapping technique to boot Windows; try replacing your Windows entry with:
```
title Windows XP
root (hd0,0)
chainloader +1
```
If you still get the same "ntldr" missing error, then please post:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Where "-l" is a lowercase L, not a one. Let me know how it goes.

---

### Post by kid_bender2000 on 2008-11-02
Thanks for your response. I figured it was time for a fresh install anyway and got it working :)

---

