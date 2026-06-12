---
title: "Files on Hard drive disappeared...."
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by cyanideoverdose on 2005-07-15
Ok I have two hard drives hda and hdd.
I wanted to get all my files off of hdd so i could remove the hard drive and put it in another computer.. 
Had everything mounted and could see my files on hdd but it wouldnt let me copy my files to hda2 (my fat32 partition). so i messed with something in /etc/fstab and was able to copy my files.. but then the files just disappeared... in mid copy.. i went to go to a folder on my hdd, and it said the folder wasnt there.. so i rebooted and now ubuntu tells me that my 6gb hdd is only 4k and empty... 

```
cyanide@overdose:/media/storage # mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hda2 on /media/backup type vfat (rw,iocharset=utf8,umask=000)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdd1 on /media/storage type vfat (rw,noexec,nosuid,nodev,umask=000)
``` 

```
cyanide@overdose:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11922    95763433+  83  Linux
/dev/hda2           12159       19457    58629217+   b  W95 FAT32
/dev/hda3           11923       12158     1895670    5  Extended
/dev/hda5           11923       12158     1895638+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdd: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1         783     6289416    b  W95 FAT32
``` 

```
cyanide@overdose:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/hda2 /media/backup vfat rw,iocharset=utf8,umask=000 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0
/dev/hdd1 /media/storage vfat rw,noexec,nosuid,nodev,umask=000 0 0
```

---

