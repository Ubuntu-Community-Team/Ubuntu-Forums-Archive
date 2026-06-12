---
title: "How do I see my other hdd's?"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by Dr_Zaius on 2005-08-16
ok:

1) I am a complete n00b to linux so go easy on me
2) This is probally a dumb question
3) I have 3 hdd's and I can only se 1 of them, how do I see the other 2!? (They appear on device manager)  ](*,) 

If you can help please do! Thx!

---

### Post by heimo on 2005-08-16
To give us more information, open terminal (Applications->System Tools->Terminal) and type these commands (post outputs):

Shows which devices are connected to your file hierarchy:
 ```

mount

``` 

Lists partitions:
 ```

sudo fdisk -l
 
``` 

Shows configuration file which has device<->mount point mappings:
```

cat /etc/fstab

``` 

Do you see any of these disks under "Places"?

---

### Post by Dr_Zaius on 2005-08-16
[QUOTE=heimo]To give us more information, open terminal (Applications->System Tools->Terminal) and type these commands (post outputs):

Shows which devices are connected to your file hierarchy:
 ```

mount

``` 

Lists partitions:
 ```

sudo fdisk -l
 
``` 

Shows configuration file which has device<->mount point mappings:
```

cat /etc/fstab

``` 

Do you see any of these disks under "Places"?[/QUOTE]
 /dev/hde1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)




Disk /dev/hdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/hde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1       14263   114567516   83  Linux
/dev/hde2           14264       14593     2650725    5  Extended
/dev/hde5           14264       14593     2650693+  82  Linux swap / Solaris

Disk /dev/hdf: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System





# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde5       none            swap    sw              0       0
/dev/hdg        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdh        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

