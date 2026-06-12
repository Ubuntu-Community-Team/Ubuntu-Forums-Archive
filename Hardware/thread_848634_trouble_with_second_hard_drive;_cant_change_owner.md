---
title: "trouble with second hard drive; cant change owner"
date: 2008-07-03
forum: Hardware
---

### Post by drzanju92 on 2008-07-03
When I go to permissions and change the owner right after I click my name the window closes. If you need anymore info just tell me.

---

### Post by sisco311 on 2008-07-03
fat, ntfs, ext2 or ext3?
internal/external?

---

### Post by drzanju92 on 2008-07-04
fat32, internal

---

### Post by sisco311 on 2008-07-04
You can't change the owner and permissions on fat and ntfs partitions.

You can setup the permissions and owner at mount time.
Open a terminal and list the partitions:
```
sudo fdisk -l
```...
/dev/sd**XY ... ... **FAT32
...

sdXY is the fat partition.
To setup the permissions you need to create a new enrty in the fstab
(or modify the old entry if exist)

First get the uuid of the partition:
```
sudo vol_id --uuid /dev/sd**XY**
```edit the fstab:
```
gksu gedit /etc/fstab
```and add this line:
> UUID=<*copy the uuid of the partition here*> /media/<mount-point> vfat defaults,umask=002,gid=46 0 0umask=002 sets the permission to 775(read/write/execute for owner, read/write/execute for group, read/execute for others)
gid=46 sets the group id to 46(plugdev)

By default, the user created during the install is member of the group plugdev(46).

If you want, you can set the owner(by default is root) with the uid option:
uid=*your-user-name*

For more info about permissions:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

For more mount options read the manual page:
```
man mount
```(q to quit)

create the <mount point> (a directory in your filesystem where you can access the partition)
```
sudo mkdir /media/<mount-point>
```replace <mount-point> with a directory name (disk, music, windows ... )

mount the partition:
```
sudo mount -a
```

---

