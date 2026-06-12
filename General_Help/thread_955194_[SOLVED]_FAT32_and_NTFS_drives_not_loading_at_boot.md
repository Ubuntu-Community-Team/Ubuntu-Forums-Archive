---
title: "[SOLVED] FAT32 and NTFS drives not loading at boot: Kubuntu Hardy 8.04.1"
date: 2008-10-22
forum: General Help
---

### Post by TWO on 2008-10-22
Hello

I have a rather annoying problem at the moment. I have made a fresh install of Kubuntu Hardy after having tried the Kubuntu Intrepid Beta for a little while.

Anyway, back to Hardy now and it is now 8.04.1 and KDE 3.5.10. I can't see any major differences but for the first time in the period that I have been using K(Ubuntu), neither the NTFS nor FAT32 partitions of my drive a loading at boot. 

I am not so bothered about the NTFS section, but I have the FAT32 section as share between my dual boot systems. 

I have followed instructions from [here]("https://help.ubuntu.com/community/Fstab") to try and get things back to normal, but even editing the /etc/fstab file has proved fruitless. After rebooting the system and clicking on the icon for the FAT 32 partition, I am presented with the window that you can see in the screenshot I have provided.

Here are the results of running ```
cat /etc/fstab
``` in Konsole:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=f6e63ea9-2ced-4bc9-9b98-291e61bf6b95 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=04473fe1-bcb8-4d10-bee5-31dc631876c5 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# /dev/sda5/
UUID="f6e63ea9-2ced-4bc9-9b98-291e61bf6b95" /media/disk vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0yoshi@igl00:~$

```

The 'sda5' entry is my manual attempt at making the partition in question boot automatically. 'sda1,' the NTFS drive doesn't even appear in the file. I have no idea why they are not automatically mounting this time. 

I don't suppose that a change in installation method would affect this? Because I currently have a broken CD drive and so I have been reinstalling via the USB method in that I use a program to make memory stick bootable. 

The very reason I chose to revert from the Intrepid Beta was because I was experiencing these mounting problems for those partitions! So you can imagine my surprise that this should be a problem on the very version I just came from!

If any one has any solutions to this problem, they would be most appreciated!

Thanks

TWO

---

### Post by TeXtonyx on 2008-10-22
Your fstab doesn't look right. ntfs-config is a tool to automatically write to fstab.
 [http://onlyubuntu.blogspot.com/2007/03/widows-ntfs-partitions-readwrite.html](http://onlyubuntu.blogspot.com/2007/03/widows-ntfs-partitions-readwrite.html)

It uses an older version of Ubuntu in the example but it works fine in Hardy.

---

### Post by dcstar on 2008-10-22
> **TWO said:**
> 
.......
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=**f6e63ea9-2ced-4bc9-9b98-291e61bf6b95** /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=04473fe1-bcb8-4d10-bee5-31dc631876c5 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# /dev/sda5/
UUID="**f6e63ea9-2ced-4bc9-9b98-291e61bf6b95**" /media/disk vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0yoshi@igl00:~$

```

The 'sda5' entry is my manual attempt at making the partition in question boot automatically. 'sda1,' the NTFS drive doesn't even appear in the file. I have no idea why they are not automatically mounting this time. 


A UUID is **unique**, no wonder you are having trouble.

Delete that line, install the **pysdm** package and use that to set up your drives.

---

### Post by TWO on 2008-10-24
> **dcstar said:**
> A UUID is **unique**, no wonder you are having trouble.

Delete that line, install the **pysdm** package and use that to set up your drives.

Haha, lame! :eek:

Only now have I realised my obvious error!! I don't even know how I made the mistake of using the same UUID but yes, I guess the reason for it **still** not working would be my own fault. I'll give the package a try and get back to you!

Thanks

TWO

---

### Post by TWO on 2008-10-24
> **dcstar said:**
> A UUID is **unique**, no wonder you are having trouble.

Delete that line, install the **pysdm** package and use that to set up your drives.

Thanks very much! Installing that package seems to have done the trick!

Any ideas why Hardy didn't set up the automatic booting of NTFS/FAT32 partitions from installation, even though it had done before 8.04.1?

I'll have to take more care when editing configuration files in future...

Thanks again!

TWO

P.S Thanks for your suggestion too TeXtonyx. I have tried ntfs-config before but I think I prefer the package the dcstar suggested!

---

### Post by TWO on 2008-10-26
Actually

I was a bit premature in thinking the problem was solved. Thanks to pysdm I am able to access my partitions but it now appears that I am unable to write to them. 

This is the current set-up of /etc/fstab via pysdm:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                              0  0
# /dev/sda6
UUID=f6e63ea9-2ced-4bc9-9b98-291e61bf6b95  /               ext3         relatime,errors=remount-ro            0  1
# /dev/sda7
UUID=04473fe1-bcb8-4d10-bee5-31dc631876c5  none            swap         sw                                    0  0
/dev/sdb1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                 0  0
/dev/scd0                                  /media/cdrom1   udf,iso9660  user,noauto,exec,utf8                 0  0
/dev/sdb                                   /media/floppy0  auto         rw,user,noauto,exec,utf8              0  0

/dev/sda5                                  /media/sda5     vfat         uid=1000,umask=000,gid=1000           0  0
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,umask=000,gid=users,ro  0  0

```

I presume that I've probably made some mistake when using pysdm; maybe I've missed a setting or something. 

If anyone has any ideas about what might be wrong with the current set up, any advice would be greatly appreciated!

Thanks

TWO

---

### Post by TWO on 2008-10-30
Problem is solved.

It was indeed due to my own error.

I found the following thread in the forum:

[http://ubuntuforums.org/showthread.php?t=955194](http://ubuntuforums.org/showthread.php?t=955194)

That should be enough for anyone else who happens to configure with pysdm in future.

I left that problem going for way too long. I hadn't expected for the partitions not to mount automatically as they had done under previous installs. Anyway, it's done now and I can cut and paste to the partition as normal.

TWO

---

