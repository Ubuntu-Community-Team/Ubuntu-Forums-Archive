---
title: "mp3 player problem"
date: 2006-04-16
forum: Hardware &amp; Laptops
---

### Post by sharperguy on 2006-04-16
Hi all

I have a Marsdigital mp3 player sd card reader.

It is detected but only if it is plugged in before booting Breezy and if I unplug it, i have to reboot before it detects it again when i plug it back in. What a pain.

Also, by 'detects' i mean appearing in /dev/sda, not /media/sd.

---

### Post by Sutekh on 2006-04-17
When you unplug devices in Linux you must make sure that they are unmounted first.  Otherwise when you plug it back in, it will not be available the same way.

The next time you start Ubuntu and the card reader is detected, can you post the output from these commands
```
mount
sudo fdisk -l
cat /etc/fstab
```

---

### Post by sharperguy on 2006-04-17
```

sharp@generichostname:~$ mount
/dev/hdb3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hda1 on /media/windows type vfat (rw,iocharset=utf8,umask=000)
/dev/hdb1 on /media/hdb1 type ext3 (rw,errors=remount-ro)
/dev/hdb5 on /media/win_c2 type vfat (rw,iocharset=utf8,umask=000)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/sda1 on /media/sd type vfat (rw)
sharp@generichostname:~$ sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2490    20000893+   c  W95 FAT32 (LBA)

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1312    10538608+  83  Linux
/dev/hdb2            1313       16146   119154105    f  W95 Ext'd (LBA)
/dev/hdb3           16147       19457    26595607+  83  Linux
/dev/hdb5            1313        9727    67593456    b  W95 FAT32
/dev/hdb6            9728       16100    51191091    b  W95 FAT32
/dev/hdb7           16101       16146      369463+  82  Linux swap / Solaris

Disk /dev/sda: 1028 MB, 1028915200 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         125     1004031    b  W95 FAT32
sharp@generichostname:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb1       /media/hdb1               ext3    defaults,errors=remount-ro 0      1
/dev/hdb5       /media/win_c2  vfat    iocharset=utf8,umask=000   0       0

```

However, I have been mounting my player mannualy with:

```
sudo mount -t vfat /dev/sda1 /media/sd 
```

and it only works if the player was pluged in to begin with

edit: I tried umounting it, unpligging it, then repluging it, then mounting it and i got: /dev/sda1 does not exist

now i havve to reboot :(

---

### Post by Sutekh on 2006-04-17
Okay one more thing to try, then I'm pretty sure I know what's going on.

Can you start Ubuntu with the SD reader plugged in and use```
sudo fdisk -l
```then unmount, unplug, then replug, then use ```
sudo fdisk -l
``` again.

I have an annoying problem with my digital audio player, in that it changes its location all the time.  Sometimes its /dev/sdc1, then if it is unplugged/replugged it changes to /dev/sdd1.

I want to see if you have the same problem too.

---

### Post by sharperguy on 2006-04-18
Before:```

sharp@somewhere:~$ fdisk -l

Disk /dev/sda: 1028 MB, 1028915200 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         125     1004031    b  W95 FAT32

```After:```

sharp@somwhere:~$ fdisk -l
sharp@somwhere:~$

```

---

### Post by Sutekh on 2006-04-18
What about when you use *sudo* fdisk -l.

When I just use fdisk without sudo I don't ever see the partition tables, for any disc.

---

### Post by sharperguy on 2006-04-19
nope, its the same exept it shows me all my hard disks as well (and after replugging it shows me the hards drives but not the sd).

---

