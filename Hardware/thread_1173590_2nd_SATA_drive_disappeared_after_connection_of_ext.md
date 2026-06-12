---
title: "2nd SATA drive disappeared after connection of external HD"
date: 2009-05-29
forum: Hardware
---

### Post by OutbackEike on 2009-05-29
Hi everyone,

i have 2 SATA drives in my system along with an older IDE that i use for XP and everything worked smoothly for months, until i tried to connect an older external drive that had not been used with the system since before the installation of the second SATA drive.

The system complained about being unable to mount the external drive, so i connected it to my windows laptop to check, worked fine - except for the drive being unable to disconnect. Windows complains it is in use by some application.

Next time i boot Linux, there's a massive complaint about the system being unable to read sdc1, superblocks, the whole shebang. Any attempts to access the unmounted drive with fsck fail utterly, ah, no, the software cries out, bad magic, could this be a zero length partition ?
Accessing backup superblocks doesn't work either.
Once after bootup, the drive mysteriously showed up, but none of the files were accessible.
The fstab simply doesn't show the drive at all, though.

Sysinfo still shows the drive as SCSI drive 3, but i cannot format or change any partitions with gparted or any other software i could find.
Windows, however, happily shows the drive, i even tried to delete the partition using windows, but the drive still doesn't show up in Linux.
I tried accessing it from a Live CD and a parallel install of 9.04 on my main drive, still nothing.
According to the SMART info during bootup, the disk is ok.

Any ideas ?

cheers
Eike

---

### Post by redmk2 on 2009-05-29
> **OutbackEike said:**
> Hi everyone,

i have 2 SATA drives in my system along with an older IDE that i use for XP and everything worked smoothly for months, until i tried to connect an older external drive that had not been used with the system since before the installation of the second SATA drive.

The system complained about being unable to mount the external drive, so i connected it to my windows laptop to check, worked fine - except for the drive being unable to disconnect. Windows complains it is in use by some application.

Next time i boot Linux, there's a massive complaint about the system being unable to read sdc1, superblocks, the whole shebang. Any attempts to access the unmounted drive with fsck fail utterly, ah, no, the software cries out, bad magic, could this be a zero length partition ?
Accessing backup superblocks doesn't work either.
Once after bootup, the drive mysteriously showed up, but none of the files were accessible.
The fstab simply doesn't show the drive at all, though.

Sysinfo still shows the drive as SCSI drive 3, but i cannot format or change any partitions with gparted or any other software i could find.
Windows, however, happily shows the drive, i even tried to delete the partition using windows, but the drive still doesn't show up in Linux.
I tried accessing it from a Live CD and a parallel install of 9.04 on my main drive, still nothing.
According to the SMART info during bootup, the disk is ok.

Any ideas ?

cheers
Eike

Eikel,

I believe that you are having problems because Linux names the partitions it discovers in the order it discovers them.  In other words: sda is the first drive  found and sdb is the second, etc.  This can (and does) change when you disconnect and later reconnect hard drives.  The use of UUID's will solve that problem in the future.

If you look at the fstab file you will see that the fixed disks partitions are ID'd by UUID.  Here is my fstab showing just that.  Note the comments:```
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c2ff646e-4884-4c77-ab85-e8e958f1422b /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=223b331e-418a-4bb1-b86e-b0c2b28abc03 /home           ext3    defaults        0       2
#
# /dev/sda4 !! manually added
UUID="d49556bd-a3d7-4c5a-a87d-4679db6817f3"     /smb            ext3    defaults        0       2
# /dev/sda2
UUID=f21ea669-94b0-4df5-bc93-b948fa986177 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

To find the UUID's on your system try this```
sudo blkid
```

This will give you a listing of UUID's.  Here is what mine loooks like```
sudo blkid
[sudo] password for redmk2: 
 
/dev/sda1: UUID="c2ff646e-4884-4c77-ab85-e8e958f1422b" TYPE="ext2" 
/dev/sda2: TYPE="swap" UUID="f21ea669-94b0-4df5-bc93-b948fa986177" 
/dev/sda3: LABEL="home" UUID="223b331e-418a-4bb1-b86e-b0c2b28abc03" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="d49556bd-a3d7-4c5a-a87d-4679db6817f3" SEC_TYPE="ext2" TYPE="ext3" 

```

As a side note to this; I have just added a new SATA drive to another machine.  Linux has decided it is sda. In front of the disk that has been in the box for the last year.  The old disk is now sdb 1-4,  Go figure.

---

### Post by OutbackEike on 2009-05-30
Hi Red,

thanks for you quick reply, i had wondered what the uuid was for. However, when i blkid my system, the drive doesn't show up there, either, so i don't know what to enter in the fstab. My blkid looks like this 

```

sudo blkid

/dev/sda1: TYPE="ntfs" UUID="CEF4DA08F4D9F2A7" 
/dev/sdb1: UUID="76c4c179-e12c-40c1-a5d1-91edca11d1ac" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="752f59e8-e5c2-42d4-a250-b4da35aa083c" 
/dev/sdb6: UUID="8117752f-5f0c-4bdc-9b25-4f26e92d3ffb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: TYPE="swap" UUID="93d55c23-5b1f-43e5-b707-600a3fe064c4" 

```It's a bit of a mess because of the parallel installment of 9.04 on the same drive as 8.04, but i can see only two different drives there and the list corresponds to everything i see using the partitionmanager or disk manager.

Is there maybe another tool that helps with that sort of thing on a deeper level than gparted or disk manager ?

thanks
Eike

P.S. : In case that's useful, here's my fstab

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sdb1 :
UUID=76c4c179-e12c-40c1-a5d1-91edca11d1ac    /    ext3    defaults,errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=CEF4DA08F4D9F2A7    /media/XP\040System    ntfs-3g    defaults,locale=de_DE.UTF-8    0    0
#Entry for /dev/sdb5 :
UUID=752f59e8-e5c2-42d4-a250-b4da35aa083c    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto    0    0


```

---

### Post by redmk2 on 2009-05-30
> **OutbackEike said:**
> Hi Red,

thanks for you quick reply, i had wondered what the uuid was for. However, when i blkid my system, the drive doesn't show up there ...


The UUID is assigned to the partition itself.  If it does not show up, I would guess that the system does not recognize it.  The system will not use that UUID again.
> 

Is there maybe another tool that helps with that sort of thing on a deeper level than gparted or disk manager ?


I don't know about deeper.  I use fdisk and mk2fs to setup my harddrives.  Since I have never used parted or gparted i can't really comment.  

With fdisk you should be able to delete the existing partition.  Using mk2fs (or mkfs.ext3) you then format the partition with a new file system.

See if you can spot the drive (partitions) in /dev.  Try this```
ls /dev | grep ^sd
```

This lists the devices and partitions available that start with *[COLOR="Red"]sd[/COLOR]*

On this host I have 1 hard drive with 4 partitions.  It looks like this```
ls /dev | grep ^sd
sda
sda1
sda2
sda3
sda4

```

---

### Post by OutbackEike on 2009-05-31
Thanks again,

after having windows complain about the drive after a complete reformat as well, i think it's just plain broken. Warranty's still valid, so hopefully, i'll get a replacement.

cheers
Eike

---

