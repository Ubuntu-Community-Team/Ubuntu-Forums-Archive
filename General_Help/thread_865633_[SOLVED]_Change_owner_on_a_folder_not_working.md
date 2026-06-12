---
title: "[SOLVED] Change owner on a folder not working"
date: 2008-07-20
forum: General Help
---

### Post by torswin on 2008-07-20
Hello

I have made a partition (/dev/sdb2) which is FAT32 and I thought that there is where I will have my music (dualbooting Vista and Ubuntu). 

So. To have this to work I thought I should change the owner of /musikk but there's a problem :(

```
torswin@Stasjonaer:~$ sudo mount /dev/sdb2 /musikk
mount: /dev/sdb2 already mounted or /musikk busy
mount: according to mtab, /dev/sdb2 is already mounted on /musikk
```
(just to make sure you guys know that it is mounted)

```
torswin@Stasjonaer:~$ sudo chown -v torswin\: /musikk
chown: changing ownership of `/musikk': Operation not permitted
failed to change ownership of `/musikk' to torswin:torswin

```

What am I doing wrong? I can copy stuff over if I am logged as root so it works.

---

### Post by scragar on 2008-07-20
```
sudo chown -v $USER /musikk
```
should work wonders.

---

### Post by sisco311 on 2008-07-20
you can't change the owner(with chown) on a fat partition.
please post the output from:
```
cat /etc/fstab
```

---

### Post by torswin on 2008-07-21
```
torswin@Stasjonaer:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=2ddfb936-489a-43f5-9475-c1d02d50bbb8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=1d2c7582-3a79-4532-b69f-688de4df2782 /musikk         ext3    relatime        0       2
# /dev/sdb1
UUID=ddaa255d-7dea-4b32-908e-96202bdb30b8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
torswin@Stasjonaer:~$ 

```

Edit:
Why does it now says that it is an ext3 partition?

---

### Post by drs305 on 2008-07-21
> **torswin said:**
> 
Why does it now says that it is an ext3 partition?

Run this to see what your system thinks the partitions are. If you just edited fstab, did you umount and mount again?
```
sudo fdisk -l
```

If you repartitioned, you may also need to check your UUIDs:
```
sudo blkid
```

---

### Post by mcduck on 2008-07-21
If the partition resally is FAT, yo can't change permissions there. FAT and NTFS filesystems are not able to handle Linux/Ubnix-style permissions and ownerships.

But since your fstab lists that as Ext3 partition, you should probably run "sudo fdisk -l" to confirm what file system itt's really using.

---

### Post by torswin on 2008-07-21
```
torswin@Stasjonaer:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefd38ce4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00053d96

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         249     2000061   82  Linux swap / Solaris
/dev/sdb2             250        6328    48829567+   b  W95 FAT32
/dev/sdb3            6329       60801   437554372+  83  Linux
torswin@Stasjonaer:~$ 

```

```
torswin@Stasjonaer:~$ sudo blkid
/dev/sda1: UUID="DE3CFBD33CFBA525" TYPE="ntfs" 
/dev/sdb1: TYPE="swap" UUID="ddaa255d-7dea-4b32-908e-96202bdb30b8" 
/dev/sdb2: UUID="4883-D990" TYPE="vfat" 
/dev/sdb3: UUID="2ddfb936-489a-43f5-9475-c1d02d50bbb8" TYPE="ext3" 
torswin@Stasjonaer:~$ 

```



But if I can't use FAT32-disks how would you suggest that I have a partition which works both in Linux and Windows?

---

### Post by sisco311 on 2008-07-21
You can set the owner, group and permissions
in the fstab. To get read/write permissions on the 
partition replace:
> UUID=1d2c7582-3a79-4532-b69f-688de4df2782 /musikk         ext3    relatime        0       2with > UUID=4883-D990 /musikk vfat defaults,umask=0002,gid=46 0 0 to edit the file:
```
gksu gedit /etc/fstab
```remount the partition:
```
sudo umount /musikk
sudo mount -a
```

---

### Post by drs305 on 2008-07-21
Nevermind, sisco311 posted same.

---

