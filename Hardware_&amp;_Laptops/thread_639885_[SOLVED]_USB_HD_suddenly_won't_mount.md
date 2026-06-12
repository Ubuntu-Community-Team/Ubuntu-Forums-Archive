---
title: "[SOLVED] USB HD suddenly won't mount"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by OliverN on 2007-12-13
All of the sudden my usb hd won't mount. The path to it is /dev/sdb2. Here's my problem: ```
$ sudo mount /media/sdb2
mount: can't find /media/sdb2 in /etc/fstab or /etc/mtab
```

This is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
 /dev/sdb1
UUID=547f36fa-ddec-4229-a119-7759dace36e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=07D6-081E  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
 /dev/sda2
UUID=866C62066C61F0FB /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
 /dev/sdb2
UUID=b27ec669-5e76-4dba-8151-a37400d0d4d9 none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

and this is my mtab:

```
/dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/sda2 /media/sda2 fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
```

any help from a friendly person?

---

### Post by taurus on 2007-12-13
> **OliverN said:**
> All of the sudden my usb hd won't mount. The path to it is /dev/sdb2. Here's my problem: ```
$ sudo mount /media/sdb2
mount: can't find /media/sdb2 in /etc/fstab or /etc/mtab
```

This is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
 /dev/sdb1
UUID=547f36fa-ddec-4229-a119-7759dace36e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=07D6-081E  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
 /dev/sda2
UUID=866C62066C61F0FB /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
 [B]/dev/sdb2
UUID=b27ec669-5e76-4dba-8151-a37400d0d4d9 none            swap    sw              0       0[/B]
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
```



Your /etc/fstab looks a little weird to me.  Is there a # in front of /dev/sdb2?  And from the look of it, shouldn't /dev/sdb2 be your swap?

Why don't you post the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by OliverN on 2007-12-13
> **taurus said:**
> Your /etc/fstab looks a little weird to me.  Is there a # in front of /dev/sdb2?  And from the look of it, shouldn't /dev/sdb2 be your swap?

Why don't you post the output of this command from a terminal?

```
sudo fdisk -l
```

I've been messing with my fstab without understanding very much of it a while back because I needed some Dell recovery partitions to not mount. 
I don't see a # in front of dev/sdb2 in my fstab, so doesn't that answer your question? My swap is sdb3 and, as far as I know, mounts correctly. This is my output of sudo fdisk -l ```
Disk /dev/sda: 78.5 Gb, 78518522880 byte
255 heads, 63 sectors/track, 9546 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d2ffbfb

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1               1          11       88326   de  Dell Værktøj
/dev/sda2   *          12        9153    73433115    7  HPFS/NTFS
/dev/sda3            9154        9545     3148740   db  CP/M / CTOS / ...

Disk /dev/sdb: 250.0 Gb, 250059350016 byte
255 heads, 63 sectors/track, 30401 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26e8f435

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdb1               1        7649    61440561   83  Linux
/dev/sdb2   *        7650       30158   180803542+   7  HPFS/NTFS
/dev/sdb3           30159       30401     1951897+  82  Linux swap / Solaris

```

---

### Post by sloggerkhan on 2007-12-13
I had this problem once, but it turned out I was mixing up the usb cables for my hd and a graphire tablet.

---

### Post by OliverN on 2007-12-13
> **sloggerkhan said:**
> I had this problem once, but it turned out I was mixing up the usb cables for my hd and a graphire tablet.

:lolflag: Well unfortunately that's not a possibility in my case as I dual-boot ubuntu from the same USB HD on which sdb2 (storage partition) is located.

---

### Post by taurus on 2007-12-13
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace the current /dev/sdb2 in there with this one.

```
/dev/sdb2   /media/sdb2   ntfs-3g   defaults   0   0
```
Save it.  Then, create a new mount point and install ntfs-3g driver so you can write to it.

```
sudo mkdir /media/sdb2
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mount -a
df -h
```

---

### Post by OliverN on 2007-12-13
> **taurus said:**
> Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace the current /dev/sdb2 in there with this one.

```
/dev/sdb2   /media/sdb2   ntfs-3g   defaults   0   0
```
Save it.  Then, create a new mount point and install ntfs-3g driver so you can write to it.

```
sudo mkdir /media/sdb2
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mount -a
df -h
```

Alright, done. In fact I only needed the directory and the new fstab entry :) The thing mounts and lets me write to it. Thank you very much for your help.

---

