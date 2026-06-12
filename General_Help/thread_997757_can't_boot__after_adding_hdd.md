---
title: "can't boot  after adding hdd"
date: 2008-11-30
forum: General Help
---

### Post by syd2o2 on 2008-11-30
Here"s my situation. I used to have one sata hdd, and I had a working dual boot setup (Ubuntu 8.04/WinXP). Then I added another sata hdd. After that neither OS would boot. So I booted the Ubuntu live cd, and did the 
find /boot/grub/stage1, setup (hd1). Now I could get to grub menu, and windows can boot. But if I select any Ubuntu entry from the list I get "Error 17: Cannot mount selected partition". Now I know it's all about selecting proper values in the menu.lst and fstab. I will post here results from fdsik -lu, my menu.lst and fstab. I've tried setting it up the way I think it should be, but then I get the no such partition message from grub. I hope someone can help me get it right, so I can boot Ubuntu again.

sda is the new hdd, ignore the linux install there. sdb is the old hdd, used to be sda. menu.lst and fstab are original values, not the versions I unsuccessfully tried. sdb is set as the boot disk in bios.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x620f0622

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1008  1433601791   716800392    f  W95 Ext'd (LBA)
/dev/sda2   *  1433601792  1485594431    25996320   83  Linux
/dev/sda3      1485594432  1493594927     4000248   82  Linux swap / Solaris
/dev/sda5            1071  1433601791   716800360+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e9a0e9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    41977844    20988891    7  HPFS/NTFS
/dev/sdb2        41977845   416854619   187438387+   f  W95 Ext'd (LBA)
/dev/sdb3       416854620   488392064    35768722+   7  HPFS/NTFS
/dev/sdb5        41977908   164859029    61440561    7  HPFS/NTFS
/dev/sdb6       164859093   369671714   102406311    7  HPFS/NTFS
/dev/sdb7       369671778   408902444    19615333+  83  Linux
/dev/sdb8       408902508   416854619     3976056   82  Linux swap / Solaris

```


menu.lst from sdb7 partiton:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=125b484d-d753-45e1-abf6-7c26085fc396 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=125b484d-d753-45e1-abf6-7c26085fc396 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=125b484d-d753-45e1-abf6-7c26085fc396 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=125b484d-d753-45e1-abf6-7c26085fc396 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=125b484d-d753-45e1-abf6-7c26085fc396 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=125b484d-d753-45e1-abf6-7c26085fc396 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


fstab form sdb7 partition:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=125b484d-d753-45e1-abf6-7c26085fc396 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=C2B86CDFB86CD407 /media/C        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=137B09C50BE00F51 /media/E        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=4DEC2718996784C4 /media/F        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=14C00DD0C00DB8CE /media/I        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=78d1f1aa-0f44-4b02-af5b-4fe56f4f2666 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```


```
find /boot/grub/stage1
 (hd0,1)
 (hd1,6)

```

---

### Post by mesastok on 2008-11-30
I had a simiral problem and i fixed it by rebuilding initrd.img-YOUR_KERNEL_HERE-generic . I don't remember how i do it. I found it on google but i cant find the link.
I remember that i have extracted it changed the drives in a file , i think init and then repackage it .
Hope to help you a bit.

---

### Post by caljohnsmith on 2008-11-30
I believe I see your problem; just change all your Ubuntu entries to use (hd0,6) instead of (hd0,7):
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,6)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=125b484d-d753-45e1-abf6-7c26085fc396 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Also, to avoid future problems when you get new kernels, also change the "groot" line:
```
# groot=(hd0,6)
```
Since Grub's numbering begins with 0, then (hd0,6) is the 7th partition, or where your Ubuntu install is. How about giving that a shot and let me know how it goes. :)

---

### Post by syd2o2 on 2008-12-01
It worked.
Thanks. 
I can't believe it was that simple.

---

### Post by caljohnsmith on 2008-12-01
It's nice when it turns out to be a simple solution, isn't it? Cheers and have fun with Ubuntu. :)

---

