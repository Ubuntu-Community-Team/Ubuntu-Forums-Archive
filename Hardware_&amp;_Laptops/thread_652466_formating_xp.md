---
title: "formating xp"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by Greensystemsgo on 2007-12-28
ok so when i installed ubuntu 7.10 last night i only partitioned my drive until i could get all the drivers working (nvidia and wlan). ok cool so now they work.

i was just looking for some quick help on how to format the xp partition and combine it with "Filesystem."

i also have a d drive that has all of my stuff on it, but its annoying how it always asks for my password when accessing... can i turn that off?

---

### Post by taurus on 2007-12-28
1.  If you want to merge your windows partition to your Ubuntu, you have to do it from a LiveCD.  Download GParted LiveCD and use that.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

2.  If you want to access your second harddrive, the best way is to add an entry in /etc/fstab so that it would be mounted automatically each time you boot Ubuntu.

What format is that second harddrive?

```
sudo fdisk -l
```

---

### Post by Greensystemsgo on 2007-12-28
my secondary drive is in NTFS. its automatically mounted, it just asks for my admin password

---

### Post by taurus on 2007-12-28
You mean you have an entry in /etc/fstab to mount your second, ntfs, harddrive?  What are the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by Greensystemsgo on 2007-12-28
```

gsg@FRANKENSTIEN5000:~$ sudo fdisk -l
[sudo] password for gsg:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x040df879

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2198    17655403+   7  HPFS/NTFS
/dev/sda2            2199        4748    20482875   83  Linux
/dev/sda3            4749        4865      939802+   5  Extended
/dev/sda5            4749        4865      939771   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefae2ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sdc: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x368b368a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3936     1007600    e  W95 FAT16 (LBA)
gsg@FRANKENSTIEN5000:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=cbebd961-a781-4b9f-bbc8-b639d6fd4712 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7f75a8a4-49d4-415b-98e9-6369012724cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
gsg@FRANKENSTIEN5000:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc1 on /media/GSG type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/sdb1 on /media/DDDDD type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
gsg@FRANKENSTIEN5000:~$ 


```

---

### Post by taurus on 2007-12-28
Have you tried to mount your /dev/sdb1 with ntfs-3g driver?

---

### Post by Greensystemsgo on 2007-12-28
btw did i mention ima noob? googling ntfs-3g driver...

---

### Post by taurus on 2007-12-28
[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

