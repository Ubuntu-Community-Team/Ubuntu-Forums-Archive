---
title: "[SOLVED] chmod chown failure"
date: 2008-09-06
forum: General Help
---

### Post by nikio on 2008-09-06
Hello,
strange things happen with my permissions;
I have a whole partition used for data storage, for all files and folders contained in it, the owner is root and group 46:
```
nik@nik-desktop:/media/Storage01/Logo P 5/Logo1_files$ ls -l
total 9
-rwxrwx--- 1 root 46  372 2007-11-16 11:40 filelist.xml
-rwxrwx--- 1 root 46 1744 2007-11-16 11:40 master03.htm
drwxrwx--- 1 root 46    0 2008-09-06 19:31 myfolder
-rwxrwx--- 2 root 46 3607 2007-11-16 11:40 slide0001_image001.gif

```

so i tried

```
nik@nik-desktop:/media/Storage01/Logo P 5/Logo1_files$ sudo chown -c nik filelist.xml 
changed ownership of `filelist.xml' to nik
nik@nik-desktop:/media/Storage01/Logo P 5/Logo1_files$ 

```

everything seems ok but

```
nik@nik-desktop:/media/Storage01/Logo P 5/Logo1_files$ ls -l
total 9
-rwxrwx--- 1 root 46  372 2007-11-16 11:40 filelist.xml
-rwxrwx--- 1 root 46 1744 2007-11-16 11:40 master03.htm
drwxrwx--- 1 root 46    0 2008-09-06 19:31 myfolder
-rwxrwx--- 2 root 46 3607 2007-11-16 11:40 slide0001_image001.gif
nik@nik-desktop:/media/Storage01/Logo P 5/Logo1_files$ 

```

nothing has changed

the same problem applies to
sudo chmod
gksudo nautilus (trying to change permissions graphically)
also with the recursive option

And more... the 46 group does not appear in the graphical "Users and Groups" utility

And more! before "46" the group was called "plugdev" and didn't appear in the list of groups in the utility, so I added it and immediately all the files became ```
-rwxrwx--- 1 root 46 ...
```

Am I doing something wrong?
Why can't I change owners and permissions?

---

### Post by aysiu on 2008-09-06
Is this an NTFS or FAT32 drive, by chance?

---

### Post by aysiu on 2008-09-06
Is this an NTFS or FAT32 drive, by chance?

---

### Post by nikio on 2008-09-06
> **aysiu said:**
> Is this an NTFS or FAT32 drive, by chance?

It's NTFS... does this affect the ownership and/or privileges?

and, anyway, I don't really understand where that "46" group comes from...

---

### Post by aysiu on 2008-09-07
You can't *chown* or *chmod* with an NTFS partition, since it doesn't support *nix permissions.

You need to mount it with NTFS-3G. I thought Ubuntu did so by default, though.

Is this an internal or external drive?

---

### Post by nikio on 2008-09-07
it is internal, mounted automatically, but now I have no access to the partition as a user, I can see the files inside only through sudo, the same thing happens with another Ntfs partition with which I didn't mess arround...

Maybe the fstab file can be useful?
the problemms I have affect all the ntfs and fat partitions

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fac2ae82-f37b-4816-b106-384400faa559 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=5b404347-6198-42d6-b3d2-138702e10534 /media/AduTemp  ext2    relatime        0       2
# /dev/sda6
UUID=E8FC62BAFC6282A4 /media/Storage01 ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=10BC4127BC4108A4 /media/Storage02 ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=288E-F739  /media/WinSwap  vfat    utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=D4A0F3A3A0F38A6E /media/WinSys   ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=c730d52f-9a80-48bf-8eb8-7c4b8ff3044b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by aysiu on 2008-09-07
I'm not really an NTFS-3g expert, but I think if you change these lines ```
UUID=E8FC62BAFC6282A4 /media/Storage01 ntfs defaults,umask=007,gid=46 0 1
# /dev/sdb1
UUID=10BC4127BC4108A4 /media/Storage02 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda5
UUID=D4A0F3A3A0F38A6E /media/WinSys ntfs defaults,umask=007,gid=46 0 1
``` to ```
UUID=E8FC62BAFC6282A4 /media/Storage01 ntfs-3g     defaults  0    0
# /dev/sdb1
UUID=10BC4127BC4108A4 /media/Storage02 ntfs-3g     defaults   0    0
# /dev/sda5
UUID=D4A0F3A3A0F38A6E /media/WinSys ntfs-3g     defaults   0    0
``` I'm also not exactly sure that NTFS-3g is installed by default (I think it is), but it couldn't hurt to double-check: ```
sudo apt-get install ntfs-3g
```

---

### Post by nikio on 2008-09-07
I think I've solved the problem changing gid=46 to gid=nik for all three partitions, now it works, but I'm not really sure if it is a correct and safe way to act.

Anyway I don't understand how were the partitions assigned to an unexisting plugdev group and, after I created it (to join it), all the partitions were assigned to to this 46 group...

And, finally is it correct that all the ntfs partitions are owned by root?

EDIT:
We posted at the same time, I have ntfs-3g installed, and in this [thread]("http://ubuntuforums.org/showthread.php?t=685880") they say that ntfs is an alias for ntfs-3g, and is some more useful advice

Thankyou for your time and suggestions!

---

