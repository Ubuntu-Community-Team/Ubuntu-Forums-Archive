---
title: "Cannot set partition to boot automatically."
date: 2008-08-12
forum: General Help
---

### Post by umanzor on 2008-08-12
Hello everyone. I have 2 physical discs and one external USB drive. First physical disk contains the windows partition and the second disk is where the ubuntu (root and every other directory) and swap partition. The USB drive contains music and movies.

Now, the USB drive is mounted automatically every time I boot, but the Windows partition isn't. I have tried to modify the fstab but I just got an unmountable partition, even though the syntax seemed to be fine.

This is the output of some commands

```
manuel@desktop:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=319858df-0f8e-4ea7-a989-0fcf6b8811a9 /               ext3    relatime,errors=remount-ro 0       1
/dev/sdb6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sda1
#UUID=565C96B15C968AFF /media/Windows/ ntfs default,errors=remount -rw 0 1
# /dev/sdc1
#UUID=C240023B40023727 /media/Media/ ntfs default,errors=remount -rw 0 1

```

```
manuel@desktop:~/Desktop$ cat mount
/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/manuel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=manuel)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=manuel)
/dev/sdd on /media/PHONE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdc1 on /media/Media type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
manuel@desktop:~/Desktop$ 
```

```
manuel@desktop:~/Desktop$ df > df
manuel@desktop:~/Desktop$ cat df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb5             28688764   6456056  20786860  24% /
varrun                  647732       116    647616   1% /var/run
varlock                 647732         0    647732   0% /var/lock
udev                    647732        72    647660   1% /dev
devshm                  647732        96    647636   1% /dev/shm
lrm                     647732     39760    607972   7% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      28688764   6456056  20786860  24% /home/manuel/.gvfs
/dev/scd0                87918     87918         0 100% /media/cdrom0
/dev/sdd                 18016       303     17713   2% /media/PHONE
/dev/sdc1            488384000 180913456 307470544  38% /media/Media
/dev/sda1            199133672  87956140 111177532  45% /media/disk
manuel@desktop:~/Desktop$ 

```

Now SDA1 is the Windows partition, SDC1 is the external USB drive, and SDD is the magicjack I use in Windows, so nvm about that one.

How can I add sda1 to fstab so it is mounted on boot?

Thanks a lot!

---

### Post by cariboo on 2008-08-12
Thanks for posting all the in formation, but could you post the output of:

```
sudo fdisk -l
```

Jim

---

### Post by umanzor on 2008-08-12
```

manuel@desktop:~/Desktop$ sudo fdisk -l > fdisk
[sudo] password for manuel: 
manuel@desktop:~/Desktop$ cat fdisk 

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009f884

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24791   199133676    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33213320

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2        4111    33013575    5  Extended
/dev/sdb5               2        3601    28916968+  83  Linux
/dev/sdb6            3602        3856     2048256   82  Linux swap / Solaris
/dev/sdb7            3857        4111     2048256    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 18 MB, 18612224 bytes
1 heads, 36 sectors/track, 1009 cylinders
Units = cylinders of 36 * 512 = 18432 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?    21614887    53323488   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(21614886, 0, 13)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(53323487, 0, 7)
Partition 1 does not end on cylinder boundary.
/dev/sdd2   ?     4685821    58464383   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(4685820, 0, 3)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(58464382, 0, 10)
Partition 2 does not end on cylinder boundary.
/dev/sdd3   ?    51941152   105719713   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(51941151, 0, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(105719712, 0, 25)
Partition 3 does not end on cylinder boundary.
/dev/sdd4   ?           1   101034070  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(101034069, 0, 12)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```


Just some notes, the Windows partition is mounted in this moment. I do it manually by going to the Places menu and selecting "200.3 GB Media".

Also, as you can see from the fstab, I tried adding sda1 and sdc0, but had to comment them because I wasn't able to mount the partitions anymore.

---

