---
title: "[SOLVED] menu.lst explanation needed, broken after update"
date: 2008-07-17
forum: General Help
---

### Post by laffinet on 2008-07-17
Hi ! 

I'm after some explanation for the menu.lst file, specifically the root=... part of it.

I just installed a system update and said "yes" when asked if I want to change the menu.lst. After that, my system wouldn't boot. It starts but seems to get stuck when loading something to do with my CD/DVD drive (not sure what exactly).

I restored my old menu.lst and had a look at the differences. The only thing I found is in the kernel line. Here's the old/working one:

```
/boot/vmlinuz-2.6.24-19-generic root=UUID=4c03d7b4-0aa6-4a65-bd46-622bce0bdd0a
```

Here's the new/not working one:

```
/boot/vmlinuz-2.6.24-19-generic root=UUID=81f8e8d9-7ec1-4bfc-8ad5-3521aa69f603
```

Question: what does the "root=..." parameter do ? I searched around a bit and thought it would specify where to find root, but then all the examples I found where more along the lines of just root=/dev/hda2. 

Thanks for any help.

---

### Post by Rocket2DMn on 2008-07-17
Can you please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
```

---

### Post by laffinet on 2008-07-17
fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76c48f32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+  83  Linux
/dev/sda2            2551        3060     4096575   82  Linux swap / Solaris
/dev/sda3            3061       19457   131708902+  83  Linux

```

cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4c03d7b4-0aa6-4a65-bd46-622bce0bdd0a /               ext3    errors=remount-ro 0       1
# /dev/sda3
UUID=627f64a8-c32c-4ca0-947b-7d1f78a16dc0 /home           ext3    defaults        0       2
# /dev/sda2
UUID=80ce16b7-bbde-4286-9116-266c46b6abac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

sudo blkid:

```
/dev/sda1: UUID="4c03d7b4-0aa6-4a65-bd46-622bce0bdd0a" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="80ce16b7-bbde-4286-9116-266c46b6abac" 
/dev/sda3: LABEL="/home" UUID="627f64a8-c32c-4ca0-947b-7d1f78a16dc0" SEC_TYPE="ext2" TYPE="ext3" 

```

---

### Post by Rocket2DMn on 2008-07-17
Yeah, restore the old file, I don't know where it got that new UUID from, but it isn't correct.  It should not have done that when you upgraded to the package maintainer's version.

---

### Post by laffinet on 2008-07-17
Thanks.

---

