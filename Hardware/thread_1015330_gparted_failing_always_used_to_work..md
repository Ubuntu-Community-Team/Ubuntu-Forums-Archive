---
title: "gparted failing ??????always used to work."
date: 2008-12-18
forum: Hardware
---

### Post by rixtr66 on 2008-12-18
Strange im trying to partition my hard drive with gparted wich has never failed me!but it keeps stopping at the point where it checks partition /sda1 after shrinking the partition?the error message is supposed to be stored in root,but when i check theres nothing there?
very odd!any ideas?
thanks
Rick
](*,)

---

### Post by taurus on 2008-12-18
Do you run gparted from a harddrive (Ubuntu)?  Are you trying to resize (either shrinking or expanding) Ubuntu?

What is /dev/sda1?

Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by rixtr66 on 2008-12-18
Actually i use a gparted disk!and /dev/sda1 is where my ubuntu install was.
see i jumped the gun and wiped the drive :oops:Ive been having problems with the file systems,i keep getting wierd looping errors?
wich suprises me because ubuntu,and slackware are both solid!
so i have ubuntu on the first partition,and slack on the second partition.
somehow i ended up with 2 swap partitions.anyway maybe this info will help with figuring out why i get filesystem errors,its anew laptop so the drive should be fine.
sudo fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8a1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            4570        9327    38218635   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda3   *           1        4376    35150188+  83  Linux
/dev/sda4            4377        4569     1550272+  82  Linux swap / Solaris
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1999 MB, 1999634432 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008fac1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         243     1951866    6  FAT16

```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2bc0d76b-6be1-4ddd-90b9-8d8812281b8a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=36d8d3fd-dc7a-4619-93c5-b3dd14c5c131 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              34G  2.6G   30G   8% /
varrun               1003M   96K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M   68K 1003M   1% /dev
devshm               1003M   12K 1003M   1% /dev/shm
lrm                  1003M   40M  964M   4% /lib/modules/2.6.24-22-rt/volatile
gvfs-fuse-daemon       34G  2.6G   30G   8% /home/rick/.gvfs
/dev/sdb1             1.9G  1.6G  318M  84% /media/disk

```
i hope this helps in some way!!!
Rick

---

