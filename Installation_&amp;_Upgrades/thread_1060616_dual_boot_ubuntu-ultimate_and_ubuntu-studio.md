---
title: "dual boot ubuntu-ultimate and ubuntu-studio"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by bootdoc on 2009-02-04
OK, I installed ubuntu-ultimate edition the other day and it ran great and probably still does but...  

I partitioned the disk so that i had 10g left for a second OS. 

 

sda1 1gig /boot
sda5 230+ gigs /home
sda3 10gig / ubuntu-ult
sda6 10gig / ubuntu-studio

I used the boot partition for both installs knowing the second would overwrite the first.  So i copied the grub/menu.lst from the first install added it to the new menu.lst after the second install.  Below is a copy of my /boot/grub/menu.lst with the first 4 kernels being those for booting ubuntu-ultimate and the following 2 kernels for studio.  

so now ubuntu-studio boots and ultimate does not.
can any one tell me how to get Ubuntu-ultimate to boot.

My /etc/fstab for both installs follow also.

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

### END DEBIAN AUTOMAGIC KERNELS LIST

fdisk -l /dev/sda

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         124      995998+  83  Linux
/dev/sda2             125       29156   233199540    5  Extended
/dev/sda3           29157       30401    10000462+  83  Linux
/dev/sda5             125       27911   223199046   83  Linux
/dev/sda6           27912       29156    10000431   83  Linux

---

### Post by lha on 2009-02-07
Hi,

It would be a good idea to post the error(s) that are reported when you try to boot ultimate edition. The error message would ease pinpointing the cause to your issues. Taking into consideration your menu.lst, fstab's, and the description of your actions, I think that the following happened: When installing studio, you formatted boot partition or overwrote ultimates kernel and other boot-related files. In the process, the uuid of sda1 was changed. You could try if changing line
uuid c12b5d20-0d81-4229-aabe-532cc04b6a34
to
uuid 62f0a32b-2300-4c5f-b812-eafaef3c9c33
in menu.lst and line
UUID=c12b5d20-0d81-4229-aabe-532cc04b6a34 /boot ext3 relatime 0 2
in ultimate's fstab to
UUID=62f0a32b-2300-4c5f-b812-eafaef3c9c33 /boot ext3 relatime 0 2
allowed you to boot ultimate. Even if these changes gave you the ability to boot ultimate, your system would still be in a strange state that would break at some point.

---

### Post by eligwd on 2011-09-27
I had the same problem but with 2 hhd's, am trying to just use one for both systems Studio 11.o4 and Regular Ubuntu 11, 64bit?

---

