---
title: "Harddisk acting weird, pls help"
date: 2008-11-21
forum: Hardware
---

### Post by dereferenced on 2008-11-21
Hi
Ok now I know this is weird, but my system is showing 2.2GB free space in all partitions.. and when one of them is full.. it shows all the partitions as full. 
Mine is 160 GB seagate, and hardly have any stuff more than 40 GB.
I have made 2 primary partitions. first for windows and second into 4 logical partitions. my fdisk -l output..

root@wisdom:/media# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028611

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2490    20000893+   b  W95 FAT32
/dev/sda2            2491       19457   136287427+   5  Extended
/dev/sda5            2491       16843   115290441    b  W95 FAT32
/dev/sda6           16844       19333    20000893+  83  Linux
/dev/sda7           19334       19457      995998+  82  Linux swap / Solaris
root@wisdom:/media# 


df output:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             19842864  16572824   2269996  88% /
varrun                  252988       116    252872   1% /var/run
varlock                 252988         0    252988   0% /var/lock
udev                    252988        60    252928   1% /dev
devshm                  252988        44    252944   1% /dev/shm
lrm                     252988     39780    213208  16% /lib/modules/2.6.24-21-generic/volatile
/dev/scd0               236238    236238         0 100% /media/cdrom0


[B]
Any help is most awaited.[/B]

---

### Post by taurus on 2008-11-21
> **dereferenced said:**
> Hi
Ok now I know this is weird, but my system is showing 2.2GB free space in all partitions.. and when one of them is full.. it shows all the partitions as full. 
Mine is 160 GB seagate, and hardly have any stuff more than 40 GB.
I have made 2 primary partitions. first for windows and second into 4 logical partitions. my fdisk -l output..

root@wisdom:/media# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028611

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2490    20000893+   b  W95 FAT32
/dev/sda2            2491       19457   136287427+   5  Extended
/dev/sda5            2491       16843   115290441    b  W95 FAT32
/dev/sda6           16844       19333    20000893+  83  Linux
/dev/sda7           19334       19457      995998+  82  Linux swap / Solaris
root@wisdom:/media# 


df output:

Filesystem           1K-blocks      Used Available Use% Mounted on
**[COLOR="Blue"]/dev/sda6             19842864  16572824   2269996  88% /[/COLOR]**
varrun                  252988       116    252872   1% /var/run
varlock                 252988         0    252988   0% /var/lock
udev                    252988        60    252928   1% /dev
devshm                  252988        44    252944   1% /dev/shm
lrm                     252988     39780    213208  16% /lib/modules/2.6.24-21-generic/volatile
/dev/scd0               236238    236238         0 100% /media/cdrom0


[B]
Any help is most awaited.[/B]

Are you talking about your root filesystem--/?

---

### Post by dereferenced on 2008-11-21
I have mounted sda1(windows), sda5 (common) and sda6 (linux root) all are acting same way(as in showing same space, *one is full, all are full*). when i tried to unmount /dev/sda1 or /dev/sda5/ or /dev/sda6 it says they are not mounted.

root@wisdom:/media# umount /media/sda1
umount: /media/sda1: not mounted
root@wisdom:/media# umount /dev/sda1
umount: /dev/sda1: not mounted
root@wisdom:/media# umount /m
media/ mnt/   
root@wisdom:/media# umount /mnt/windrive/
umount: /mnt/windrive/: not mounted


root@wisdom:/media# umount /dev/sda1
umount: /dev/sda1: not mounted
root@wisdom:/media# umount /media/sda1
umount: /media/sda1: not mounted
root@wisdom:/media# umount /mnt/windrive/
umount: /mnt/windrive/: not mounted


where am I doing wrong. please help. thanks in advance.

---

### Post by taurus on 2008-11-21
How do you mount the two fat32/vfat partitions?  Do you mount them from /etc/fstab?

```
cat /etc/fstab
sudo blkid
```

---

### Post by dereferenced on 2008-11-24
root@wisdom:/# cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=36b3e94e-9f85-4be0-b461-8609cb805f79 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=464E-E478  /dev/sda1       vfat    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=8064-32EB  /dev/sda5       vfat    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=9021bec6-8f61-46ea-badd-508e53040a91 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
root@wisdom:/# blkid
/dev/sda1: UUID="464E-E478" TYPE="vfat" 
/dev/sda5: UUID="8064-32EB" TYPE="vfat" 
/dev/sda6: UUID="36b3e94e-9f85-4be0-b461-8609cb805f79" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="9021bec6-8f61-46ea-badd-508e53040a91" 


thanks in advance.

---

### Post by annda on 2008-11-24
your df output tells me that the win & shared partitions are not mounted. how do you access the files on them?

also, the mountpoints in fstab do not seem correct. please change the /dev/sda1 and /dev/sda5 mountpoints to something like /media/windows and /media/common and make sure that the mountpoints exist in the /media directory. if not

```
sudo mkdir /media/windows
sudo mkdir /media/common

```

then remount the partitions using 
```
sudo mount -a
```

does this solve the problem?

---

### Post by dereferenced on 2008-12-02
that's right I was only trying to umount it but didnt try to re-mount it. Thanks anyways it helped. I just mounted it again and it works.. not sure how it got umounted in the first place.

---

### Post by dereferenced on 2008-12-02
I now get it, after changing fstab for read-write access on /media/common, the volume got umounted automatically.. changed the below lines..

# /dev/sda1
UUID=464E-E478  /dev/sda1       vfat    **user,rw**,default,umask=0,uid=1000,gid=1000 0       1
# /dev/sda5
UUID=8064-32EB  /dev/sda5       vfat    **user,rw**,default,umask=0,uid=1000,gid=1000 0       1

after mounting again the volume has the same issues showing all the volumes of same size..

---

### Post by taurus on 2008-12-02
> **dereferenced said:**
> I now get it, after changing fstab for read-write access on /media/common, the volume got umounted automatically.. changed the below lines..

# /dev/sda1
UUID=464E-E478  **[COLOR="Blue"]/dev/sda1[/COLOR]**       vfat    **user,rw**,default,umask=0,uid=1000,gid=1000 0       1
# /dev/sda5
UUID=8064-32EB  **[COLOR="Blue"]/dev/sda5[/COLOR]**       vfat    **user,rw**,default,umask=0,uid=1000,gid=1000 0       1

after mounting again the volume has the same issues showing all the volumes of same size..

I have to still search on this.. sigh

Those in blue should be mount points, not devices.  So, change them to

/dev/sda1 -> /media/sda1
/dev/sda5 -> /media/sda5

Then, create two new mount points and remount them or reboot.

```
sudo mkdir /media/sda1 /media/sda5
sudo mount -a
df -h
```

---

### Post by dereferenced on 2008-12-03
Perfect. Thank you.

---

