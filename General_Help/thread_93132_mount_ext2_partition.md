---
title: "mount ext2 partition"
date: 2005-11-21
forum: General Help
---

### Post by dajomu on 2005-11-21
I am wondering why the heck kubuntu wont mount my ext2 partition with write access for all users. How to I change the fstab to write access for this partition?

my fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/sda3       /media/sda3     ext2    defaults        0       2
/dev/sda4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

By the way I think kubuntu messed up my partitions so now I lost the data on one of them. Anyone experienced anything like that?

---

### Post by samx on 2005-11-21
When you mount unix filesystem you can't define who should be able to read or write it, because the filesystem has attributes which define that.
You can mount it read-only, than nobody can write to it, but if you mount it read-write, the standard unix file system attributes decide who can write to it.
So open a shell and try
```
cd /media/sda3
ll
```
There you'll the the owner and the permissions for the files.
You can change the owner with
```
chown [-R] user:group files
```
or you can change the attributes with
```
chmod [options] files
```
(Another reason could be that the permissions of the folder /media/sda3 itself are wrong, then you have to change them so that you can read and write there)

---

