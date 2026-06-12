---
title: "Hard Drive Formatting"
date: 2009-01-09
forum: Hardware
---

### Post by jhoffman1986 on 2009-01-09
I'm trying to share an external hard drive to be utilized by my Ubuntu laptop, Windows desktop, and Xbox 360.  I was able to use it with the Ubuntu and Windows, but I'm not able to use it to play my media through my 360 (I'm not trying to use it to store 360 files, but only to play media files on the 360).

Unfortunately, my 360 isn't recognizing the drive when I plug it in.  I looked online, and it appears (unless I'm mistaking something) that the drive needs to be "FAT32"?  If that's the case, will a FAT32 external (usb 2.0) still work with both Windows and Ubuntu, and more importantly, HOW do I format a drive to FAT32?

If there's a different way, and I have the wrong info, feel free to let me know.  This is from google searching and whatnot, as well as trying to find an answer in these forums.

---

### Post by jhoffman1986 on 2009-01-10
Anybody have any ideas on this?  Or on another note, another type of hard drive formatting that can be used by Ubuntu, Windows, and a 360?  I tried formatting in FAT32 from windows, but it's 80gb, so it gave me a "drive too large" error?

Now I'm hearing that HFS+ might work, but I've never even heard of that, much less know how to make it happen?

---

### Post by vanadium on 2009-01-10
fat32 is most compatible. MS Windows does not give you the freedom to format large volumes in fat32, but there is Ubuntu to the rescue

```

mkfs -t vfat /dev/sd?

```

or use gparted.

If the xbox also reads ntfs, you might prefer to format the drive in ntfs, though.

---

### Post by jhoffman1986 on 2009-01-11
Tried using your shell command, my external being sdb, but I keep getting the following error message.

julian@julian-laptop:~$ sudo mkfs -t vfat /dev/sdb
[sudo] password for julian: 
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /dev/sdb


Any idea what I'm doing wrong?  Also tried deleting the partition in Gparted and making a new one, but didn't see a fat32 or fat partition.  Have no idea how to use gparted, or what I'm doing wrong :-\

---

### Post by Gillingham on 2009-01-11
From what I understand /dev/sdb will point to the whole drive rather than to a particular partition.  The first partition on sdb will be sdb0 and other partitions will be numbered sequentially so sdb1, sdb2 etc. So try

```
sudo mkfs -t vfat /dev/sdb0
```

---

### Post by vanadium on 2009-01-11
To see the device names of the partitions on your drives, use one of the commands "sudo blkid" or "sudo fdisk -l"

---

### Post by jhoffman1986 on 2009-01-11
Thanks guys.  I kept typing sdb instead of sdb1.  Quick terminal command fix and it worked.

---

