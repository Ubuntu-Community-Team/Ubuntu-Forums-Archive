---
title: "dual booting 2 ubuntus"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by bootdoc on 2009-02-05
I want to boot 2 ubuntu distros on my machine.  I installed Ubuntu-Ultimate and made a copy of the /boot/grub/menu.lst in my home partition.  I then installed ubuntu-studio using the same /home and /boot partitions.  I pasted the menu.lst that i copied to the new /boot/grub/menu.lst.  Now when I try to boot UUE I get grub error 15 file not found.  below is the grub menu, /etc/fstab from both root partitions and fdisk-l /dev/sda.

title           Ubuntu 8.10, kernel 2.6.27-11-generic
uuid            62f0a32b-2300-4c5f-b812-eafaef3c9c33 
kernel          /vmlinuz-2.6.27-11-generic root=UUID=0aa4f67b-626a-42c4-8d83-b60ed1e3dea9 ro quiet splash vga=792 
initrd          /initrd.img-2.6.27-11-generic                                                                     
quiet                                                                                                             

title           Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid            62f0a32b-2300-4c5f-b812-eafaef3c9c33
kernel          /vmlinuz-2.6.27-11-generic root=UUID=0aa4f67b-626a-42c4-8d83-b60ed1e3dea9 ro  single
initrd          /initrd.img-2.6.27-11-generic

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            62f0a32b-2300-4c5f-b812-eafaef3c9c33
kernel          /vmlinuz-2.6.27-7-generic root=UUID=0aa4f67b-626a-42c4-8d83-b60ed1e3dea9 ro quiet splash vga=792
initrd          /initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            62f0a32b-2300-4c5f-b812-eafaef3c9c33
kernel          /vmlinuz-2.6.27-7-generic root=UUID=0aa4f67b-626a-42c4-8d83-b60ed1e3dea9 ro  single
initrd          /initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            62f0a32b-2300-4c5f-b812-eafaef3c9c33
kernel          /memtest86+.bin
quiet


title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c12b5d20-0d81-4229-aabe-532cc04b6a34
kernel		/vmlinuz-2.6.27-7-generic root=UUID=6cb5ac6f-91cb-4665-9b64-ebf3c3b385ab ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c12b5d20-0d81-4229-aabe-532cc04b6a34
kernel		/vmlinuz-2.6.27-7-generic root=UUID=6cb5ac6f-91cb-4665-9b64-ebf3c3b385ab ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c12b5d20-0d81-4229-aabe-532cc04b6a34
kernel		/memtest86+.bin
quiet

Ubuntu-ultimate
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=0aa4f67b-626a-42c4-8d83-b60ed1e3dea9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=62f0a32b-2300-4c5f-b812-eafaef3c9c33 /boot           ext3    relatime        0       2
# /dev/sda5
UUID=c8705f25-f20d-4680-b6c7-66d84158bb5d /home           ext3    relatime        0       2
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Ubuntu-studio
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6cb5ac6f-91cb-4665-9b64-ebf3c3b385ab /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=c12b5d20-0d81-4229-aabe-532cc04b6a34 /boot           ext3    relatime        0       2
# /dev/sda5
UUID=c8705f25-f20d-4680-b6c7-66d84158bb5d /home           ext3    relatime        0       2
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         124      995998+  83  Linux
/dev/sda2             125       29156   233199540    5  Extended
/dev/sda3           29157       30401    10000462+  83  Linux
/dev/sda5             125       27911   223199046   83  Linux
/dev/sda6           27912       29156    10000431   83  Linux

---

### Post by Tim Sharitt on 2009-02-07
I'm not really sure which entry you are having trouble booting, but here are some tips to help get things sorted out.

I'm Just using one of your entries as an example.
```

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid c12b5d20-0d81-4229-aabe-532cc04b6a34
kernel /vmlinuz-2.6.27-7-generic root=UUID=6cb5ac6f-91cb-4665-9b64-ebf3c3b385ab ro single
initrd /initrd.img-2.6.27-7-generic
```

Where you see uuid in the second line, this should be the the uuid of the partition where your kernel image and initrd reside. You can also use 
```
root (hdx,y)
```
replacing x with the drive number (starting with zero) and y with the partition number (also starting with zero).

The path for the kernel and initrd start with the root of the partition provided by uuid or root. If you are using a dedicated boot partition, for the kernel you would use 
```
/vmlinuz-(version)
```
and the same for the initrd
```
/initrd-(version)
```

If you didn't install with a dedicated boot partition, the kernel image and initrd files would be in the boot folder of the root directory.
To use these files, you would need to give the full directory. 

For kernel
```
/boot/kernel-(version)
```

and for initrd
```
/boot/initrd-(version)
```

On the same line as kernel there is a line for root=UUID=6cb5ac6f-91cb-4665-9b64-ebf3c3b385ab.
This uuid string needs to be the uuid of the root file system of the system you are booting. It will not be the same as the uuid string above if you are using a different boot partition. You can also use root=(hdx,y) instead of the UUID.

I hope this helps. Feel free to post any other questions you may have.

---

