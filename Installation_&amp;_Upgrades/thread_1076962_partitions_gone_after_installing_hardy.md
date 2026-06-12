---
title: "partitions gone after installing hardy"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by abhinav.p on 2009-02-21
1)before reinstalling hardy my harddrive had 8 partitions.after installation in one of the partitions,the 8 partitions were made 4 because of the packaged distribution i used.but the data was not lost.it was lumped up in 4 partitions.how can i get back my 8 partions?
2)fstab shows only /proc mounted.
3)how do the set the partitions to mount automatically after booting?

---

### Post by taurus on 2009-02-22
Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by abhinav.p on 2009-02-22
abhinav@raphtor:~$ sudo fdisk -l
[sudo] password for abhinav: 

OUTPUT FOR FDISK:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12        1286    10241437+   c  W95 FAT32 (LBA)
/dev/sda3            1287        2561    10241437+  83  Linux
/dev/sda4            2562       30401   223624800    f  W95 Ext'd (LBA)
/dev/sda5            2562        6385    30716248+   b  W95 FAT32
/dev/sda6            6386       10131    30089713+   b  W95 FAT32
/dev/sda7           10132       15158    40379346   83  Linux
/dev/sda8           15159       22993    62934606   83  Linux
/dev/sda9           22994       30401    59504728+   7  HPFS/NTFS


OUTPUT FOR cat /etc/fstab
abhinav@raphtor:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6672cdf4-916a-44d6-a335-e33489a8e0a2 /               ext2    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0




OUTPUT FOR df -h:
abhinav@raphtor:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             9.7G  2.4G  6.8G  26% /
varrun               1009M  120K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   68K 1009M   1% /dev
devshm               1009M   12K 1009M   1% /dev/shm
lrm                  1009M   38M  972M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      9.7G  2.4G  6.8G  26% /home/abhinav/.gvfs
/dev/sda5              30G   21G  9.0G  70% /media/STUFF
/dev/sda6              29G   12G   18G  40% /media/disk

---

### Post by viksmicro on 2009-02-22
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b9f32f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+  82  Linux swap / Solaris
/dev/sda2            4865       14593    78148192+   f  W95 Ext'd (LBA)
/dev/sda5            4865        9728    39070048+  82  Linux swap / Solaris
/dev/sda6            9729       14593    39078081   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ca88903

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
viksmicro@vikas-laptop:~/Documents/essential-20071007$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=970cda9d-7e88-46a9-ab33-a0a1be62898c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=caf2ddd0-f923-4444-b3d9-686c85156f6d none            swap    sw              0       0
# /dev/sda5
UUID=746ed5ab-b1a6-4e97-bbd7-ccefccad7b85 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
viksmicro@vikas-laptop:~/Documents/essential-20071007$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              37G  2.4G   33G   7% /
tmpfs                 500M     0  500M   0% /lib/init/rw
varrun                500M   96K  500M   1% /var/run
varlock               500M     0  500M   0% /var/lock
udev                  500M  2.8M  498M   1% /dev
tmpfs                 500M   12K  500M   1% /dev/shm
lrm                   500M  2.0M  499M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdb1             466G  149G  317G  32% /media/GK

---

