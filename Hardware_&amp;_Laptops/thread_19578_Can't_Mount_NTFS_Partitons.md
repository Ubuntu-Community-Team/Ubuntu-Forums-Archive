---
title: "Can't Mount NTFS Partitons"
date: 2005-03-12
forum: Hardware &amp; Laptops
---

### Post by Seandq on 2005-03-12
*gasp*  A new one. I've searched and no one really answered my error. My fdisk -l still lists my /dev/hda1 intact as shown below:

[quote=fdisk -l]
Disk /dev/hda: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2490    20000893+   7  HPFS/NTFS

Disk /dev/hdd: 30.7 GB, 30750031872 bytes
16 heads, 63 sectors/track, 59582 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       37406    18852246    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdd2           44928       56706     5936017+  83  Linux
/dev/hdd3           37407       44927     3790584   83  Linux
/dev/hdd4           56706       58730     1020127+   5  Extended
/dev/hdd5           56706       58730     1020096   82  Linux swap

Partition table entries are not in disk order
[/QUOTE]

I believe that my hda1 could've been altered when I, in FC3 rescue mode, hit 'grub-install /dev/hda' instead of my MBR on /dev/hda1. Ubuntu didn't seem to notice Windows, nor did the recovery console on Win32's disk.

What happens when I attempt to mount is the following error message:

> sean@ubuntu:~ $ sudo mount -t ntfs -o umask=0222 /dev/hda1 /mnt/win_c
[B]mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       or too many mounted file systems[/B]


Wrong FS type? Nah..positive it's NTFS, it's a WinXP drive.
Bad option? Nope.
Bad superblock? Unsure.
Too many mounted filesystems? Check out my 'mount'.

[quote=mount]/dev/hdd2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hdd3 on /home type ext3 (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=sean[/quote]

So, my question is..what happened? Do I need to reinstall Windows? Could my /dev/hda1 be salvaged without a Win32 reinstall or can my files on Win32 stay the same without a Win32 reinstall?

Thanks. I just don't want my dad to think I royally screwed up windows. And to prove my 'mount' point, /dev/hdd1 works just fine.

-Sean

---

### Post by Seandq on 2005-03-12
[QUOTE=Seandq]*gasp*  A new one. I've searched and no one really answered my error. My fdisk -l still lists my /dev/hda1 intact as shown below:



I believe that my hda1 could've been altered when I, in FC3 rescue mode, hit 'grub-install /dev/hda' instead of my MBR on /dev/hda1. Ubuntu didn't seem to notice Windows, nor did the recovery console on Win32's disk.

What happens when I attempt to mount is the following error message:



Wrong FS type? Nah..positive it's NTFS, it's a WinXP drive.
Bad option? Nope.
Bad superblock? Unsure.
Too many mounted filesystems? Check out my 'mount'.



So, my question is..what happened? Do I need to reinstall Windows? Could my /dev/hda1 be salvaged without a Win32 reinstall or can my files on Win32 stay the same without a Win32 reinstall?

Thanks. I just don't want my dad to think I royally screwed up windows. And to prove my 'mount' point, /dev/hdd1 works just fine.

-Sean[/QUOTE]
 No worries, I've just reinstalled Windows XP to my parents dismay. I sware, ma and pa, I wasn't trying to rid us of Redmond!

Whatever, I must keep WinXP, me supposes.

---

