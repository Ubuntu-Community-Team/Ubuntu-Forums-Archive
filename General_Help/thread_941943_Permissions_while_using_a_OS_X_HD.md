---
title: "Permissions while using a OS X HD"
date: 2008-10-08
forum: General Help
---

### Post by Killtodie on 2008-10-08
I am trying to use Ubuntu to do a data backup of a friend Macbook. I hooked up the HD and when I try to access the docs under users its locked out and tells me I dont have permissions.

How can I assume permissions of the folder so I can access it.

---

### Post by Killtodie on 2008-10-08
tried using ```
chmod u=rw,go= /media/xh/Users/admin
``` but that doesnt work, it set as read only

---

### Post by bodhi.zazen on 2008-10-08
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: 
[list=number]
[*]vfat (FAT) use dmask=027,fmask=137
[indent]more permissive permissions : dmask=000,fmask=111[/indent]
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent]
[/list]


_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)
[indent]Vista: Install the fs-driver using the "Windows XP compatibility mode"[/indent]

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by Killtodie on 2008-10-08
using your 777 command i still get the read only file system "error"

---

### Post by Killtodie on 2008-10-08
does anyone gave any more info on this? I really need to get this backed up

---

### Post by Killtodie on 2008-10-09
How can you do a data backup on a encrypted OSX HD?

---

### Post by bodhi.zazen on 2008-10-09
What file system is it ?

---

### Post by Killtodie on 2008-10-10
Whatever was on OS9. FS or whatever its called, not the plus.

---

### Post by bodhi.zazen on 2008-10-10
Looks like the file system is hfs

see [http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

unmount the file system

Then mount it with :

```
mount /dev/sdxy /media/mount_point -o uid=1000,gid=100,umask=007
```

change "dev/sdxy" the the appropriate partition
change "/media/mount_point" to the appropriate mount point

---

### Post by phidia on 2008-10-10
It probably beside the point but a macbook would not be able to run OS 9 and would definately not be using HFS. Macbooks and all recent macs are using HFSplus.

---

### Post by bodhi.zazen on 2008-10-10
```
sudo mount -t hfsplus /dev/sdxy /media/mount_point -o uid=1000,gid=100,umask=007
```It really depends on the file system.

Try gparted or ```
sudo fdisk -l
``` to see the filesystem.

---

### Post by Killtodie on 2008-10-11
when I dismount it and run the code, it tells me that it cant find the mount point.

---

### Post by bodhi.zazen on 2008-10-11
cahnge "mount_point" to the actual mount point. 

If you do not have one, make one :

```
sudo mkidr /media/OSX
```

Then mount to /media/OSX

---

### Post by mister_doctor on 2008-12-24
[QUOTE=bodhi.zazen;5944135]```
sudo mount -t hfsplus /dev/sdxy /media/mount_point -o uid=1000,gid=100,umask=007
```

Am I correct to assume that the numbers in uid and gid must match those of your user account?

Like, if I have a user account with sudoer rights with a uid of 1001 and a gid of 1001, my version of the mount command would look like:

```
sudo mount -t hfsplus /dev/sda3 /media/osx -o uid=1001,gid=1001,umask=007
```

Y/N?

---

### Post by bodhi.zazen on 2008-12-24
yes

---

### Post by tripdr on 2009-01-22
a bit of help here. I belive I have the same issue and after hours of research I am ready to format my question.

I am running this code to mount and unmount and no matter what I try I can not get the external HD thats hfsplus to give me write access. 

I am booting from a live cd on a power mac. 

```

sudo umount /media/OSX

sudo mount -t hfsplus /dev/sdc3 /media/OSX -o uid=1000,gid=1000,umask=07

```

I have tried umask=0777 and 02 002
gid at 1001 and 0 and 100 
I am sooo lost at this point and need some sleep. 

Thank you for any help you can offer.

---

