---
title: "gparted wont read my ubuntu partition"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by pavel989 on 2008-01-03
gparted wont read dev sda1, which is my boot partition, it says it cant find the mount point. idk  how to deal with this

---

### Post by taurus on 2008-01-03
Do you run gparted from a LiveCD or from Ubuntu?  What are the outputs of these commands from a terminal if you run Ubuntu from your harddrive?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by pavel989 on 2008-01-03
```
pavel@pavel-desktop:~$ sudo fdisk -l
[sudo] password for pavel:

Disk /dev/sda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eec90

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3579    28748286   83  Linux
/dev/sda2            3736        4982    10016527+  83  Linux
/dev/sda3            3580        3735     1253070    5  Extended
/dev/sda5            3580        3735     1253038+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          10       80293+   0  Empty
/dev/sdb2              11        3648    29222235    b  W95 FAT32
```

```

pavel@pavel-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=78CB-9F80  /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c212304f-633c-4f1b-ad3e-0f69c3e118d7 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```


```
pavel@pavel-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
varrun                252M  124K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   68K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb2              28G   16G   12G  58% /media/PAVEL'S IPO
/dev/sda2             9.5G  7.4G  1.7G  82% /media/disk
```

ps, Jacksonville is great and i like ur signature

---

### Post by taurus on 2008-01-03
Looks to me like your first harddrive is now known as /dev/sda instead of /dev/hda.  So, you have two options.

1.  Determine the new UUID for /dev/sda1 and replace the old one in /etc/fstab with the right one.

or

2.  Edit /etc/fstab and replace the UUID, UUID=78CB-9F80,  for /dev/sda1 (it says /dev/hda1 in there right now) with /dev/sda1.

```
/dev/sda1   /   ext3   defaults,errors=remount-ro   0  1
```

Let's have a look at your swap too.

```
free
```


p.s.  It would be even greater if the Jags win on Saturday night!

---

### Post by pavel989 on 2008-01-04
free
             total       used       free     shared    buffers     cached
Mem:        515460     501728      13732          0       6664     107968
-/+ buffers/cache:     387096     128364
Swap:      1253028     114316    1138712


and i changed it to sda1 but gparted is still telling me i t cant find the mount point. how do i find a uuid?

---

