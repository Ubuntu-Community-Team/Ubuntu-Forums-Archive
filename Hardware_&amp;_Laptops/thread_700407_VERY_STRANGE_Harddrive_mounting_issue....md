---
title: "VERY STRANGE Harddrive mounting issue..."
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by akalberm on 2008-02-18
OK, I have not found anything like this before so I figured I would see if anyone has run into a similiar issue

I just finished installing kubuntu 7.1 on my desktop (i already install on my laptop).  I had 3 internal harddrives - 1 OS harddrive with 2 partitions (one windows and one kubuntu), and 2 NTFS storage drives.  I also have an external NTFS storage drive.

I modified the fstab file so that the two internal harddrives automount.  This was working fine for awhile (~2 reboots).  Then, I attempted to edit the fstab so that the external HD would always mount.  This worked for the first reboot.  Now when I reboot something strange happens... When I attempt to view the contents on any of them, one harddrive shows it's true contents, but the other two (other internal data drive and external data drive) show the contents of the 1 internal drive, not their own data...  VERY STRANGE!  

Anyone know what I may have done wrong and how to fix it?  I checked the harddrives in windows and no data has been deleted because all the harddrives show their true content...

---

### Post by sisco311 on 2008-02-18
please post the output from:

```
mount
``````
sudo fdisk -l
``````
cat /etc/fstab
```

---

### Post by akalberm on 2008-02-18
adam@bigboy:~$ mount
/dev/sdc2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media type fuseblk (rw,noexec,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
adam@bigboy:~$ sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39b33d63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20023   160834716    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07e2f335

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   42  SFS

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbc7dbc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdc2            2551        8768    49946085   83  Linux
/dev/sdc3            8769        9039     2176807+   5  Extended
/dev/sdc5            8769        9039     2176776   82  Linux swap / Solaris
adam@bigboy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=77c95a9a-b0bf-4fdb-876f-369085368a61 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=67154ac7-0a6f-46c4-9908-a3ea53605abd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1       /media/         ntfs    defaults,user 0       0
/dev/sda1       /media/         ntfs    defaults,user 0       0
/dev/sdd1       /media/         ntfs    defaults,user 0       0


Here is what i have right now... I do not have the external harddrive, which is sdd1 plugged in

---

### Post by sisco311 on 2008-02-18
to mount 3 partitions you need 3 folders(mount points). from the terminal you can use the mkdir command to create a directory. 

```
sudo mkdir /media/sda1
sudo mkdir /media/sdb1
sudo mkdir /media/sdd1
```edit your fstab:

```
sudo gedit /etc/fstab
```>  # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=77c95a9a-b0bf-4fdb-876f-369085368a61 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=67154ac7-0a6f-46c4-9908-a3ea53605abd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
[B] /dev/sdb1       /media/sdb1         ntfs    defaults,user 0       0
/dev/sda1       /media/sda1 ntfs    defaults,user 0       0
/dev/sdd1       /media/sdd1 ntfs    defaults,user 0       0[/B]remount your partitions:

```
sudo umount /dev/sdb1 /dev/sda1 /dev/sdd1
sudo mount -a
```done

*edit: you can change the directory names to whatever you want (ex. /media/music or /media/windows)

---

### Post by akalberm on 2008-02-18
Thank you very much - I guess the issue was not so strange after all!!!  Worked like a charm!!  Only thing to make sure is that you have your drives unmounted when your running the mkdir commands...

Thanks again!

---

