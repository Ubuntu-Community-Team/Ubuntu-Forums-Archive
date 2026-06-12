---
title: "Disk"
date: 2008-09-19
forum: General Help
---

### Post by Brunno Silva on 2008-09-19
I used to have a 8.04 32-bits Ubuntu installed in my 64-bits laptop. I divided the HD in two partitions, one for the OS and one for my files (from now on, I'll refer to the second partition as "disk"). After some problems, I formatted my SO partition and installed a 8.04 64-bits Ubuntu, but I didn't configure the mount point for disk. Now, when the SO starts, it doesn't find the disk. I have to manually provide a mount point. Do you have any idea how can I make Ubuntu do it automatically at startup?

---

### Post by zvacet on 2008-09-19
```
cat /etc/fstab
```

Post it here.

---

### Post by Rocket2DMn on 2008-09-19
Can you also please post
```
sudo fdisk -l
sudo blkid
mount
```

---

### Post by Brunno Silva on 2008-09-20
```
brunno@brunno-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=66ef6947-aa05-48bf-a507-cdc32c9d4f07 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=b1b3430e-b6b6-4cc2-9043-721243732844 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
```

brunno@brunno-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2289a1b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1052226   82  Linux swap / Solaris
/dev/sda2   *         132        2089    15727635   83  Linux
/dev/sda3            2090       14593   100438380   83  Linux
```

```
brunno@brunno-laptop:~$ sudo blkid
/dev/sda1: TYPE="swap" UUID="b1b3430e-b6b6-4cc2-9043-721243732844" 
/dev/sda2: UUID="66ef6947-aa05-48bf-a507-cdc32c9d4f07" TYPE="ext3" 
/dev/sda3: UUID="9cd9cc3d-1203-4f79-af33-ecf89fc7dc7a" SEC_TYPE="ext2" TYPE="ext3" 
```
```

brunno@brunno-laptop:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/brunno/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brunno)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
```

---

### Post by Rocket2DMn on 2008-09-20
OK, let's create an fstab entry for your data partition, we will call the mount point "data" which will mount at /media/data but you can change that if you want (no spaces in the name please).
First create the mount point, then open fstab for editing
```
sudo mkdir /media/data
gksudo gedit /etc/fstab
```
Now add this line to the bottom
```
UUID=9cd9cc3d-1203-4f79-af33-ecf89fc7dc7a /media/data ext3 defaults 0 2
```
Save and close, then mount with
```
sudo mount -a
```
The drive should automount at boot now.

---

### Post by Brunno Silva on 2008-09-20
Everything's working fine now. Thanks! ;D

---

