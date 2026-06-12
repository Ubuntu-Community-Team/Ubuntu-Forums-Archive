---
title: "Renaming Harddisks"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by Flavian on 2006-12-20
Hi folks.
I got a little problem, maybe it sounds very newbieish :( I am sorry if so...
But anyways, I know that every harddisc has it's mountpoint like /media/hdb1 and the /dev/hdb1 as well.
I don't want to change those, I know how to do that, I just want to change the NAMES they are displayed with.
For example I have a FAT32 partition which is displayed as "EXT200" because I gave it the name in windows, at some point. Now I don't have windows anymore and I want it to be displayed otherwise.
I also got an EXT3 disk in my pc and want it to be displayed with a certain name on the desktop for example... how do I do that in Linux?

Thanks in advance
Flo

---

### Post by ingo on 2006-12-22
> I know that every harddisc has it's mountpoint like /media/hdb1 and the /dev/hdb1 as well. I don't want to change those, I know how to do that, I just want to change the NAMES they are displayed with.

You know how to do that? I'd be interested to hear.

As for your particular problem - I take it you have the icon for the hard drive on your desktop. Now simply right click on it, select properties and give it any name under the sun.

---

### Post by yabbadabbadont on 2006-12-22
For ext2 and ext3 filesystems, you can change the filesystem label using "tune2fs -L newlabel /dev/XXXX", where XXXX is replaced with the correct device for that partition.  I think that the "mlabel" command from the mtools package can change the volume label of fat partitions.  I've actually used the tune2fs program to change the labels on some ext3 partitions, but I've never tried changing a fat volume label using mtools, so you might want to do some research before you try that.

---

### Post by Chipmaster on 2007-03-08
Sorry to dig this topic up, but I'm having a similar problem except the posted solution doesn't seem to work for me.

My specific issue is that a hard drive link to a FAT32 drive was renamed mysteriously to erosmith.co (which I believe is Aerosmith.com with the beginning and ending characters truncated, but don't ask me why Aerosmith has invaded my computer :guitar: ; although it might have to do with the music that's stored on this drive).  When I go to right click it, I cannot edit the name.  After thinking for a bit, I think it may have to do with the "owner" of the drive which for me is root, and the group is plugdev (which I added myself and root to under system:Administration:Users and Groups).  

Here are some useful outputs and pics (and it's /dev/hda5):

```
u@u:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3916    31455238+  83  Linux
/dev/hda2            3917       19457   124833082+   5  Extended
/dev/hda5            3917       19196   122736568+   b  W95 FAT32
/dev/hda6           19197       19457     2096451   82  Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1243     9984366    7  HPFS/NTFS
patrick@Chipmaster1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/dev/hda1 / ext3 defaults,errors=remount-ro 0 1

/dev/hda5 /media/swap vfat defaults,utf8,umask=0000,gid=46 0 1

/dev/hdb1 /media/windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1

/dev/hda6 none swap sw 0 0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

[[img]http://s11.photobucket.com/albums/a190/chipmaster/th_erosmith.png[/img]](http://i11.photobucket.com/albums/a190/chipmaster/erosmith.png?t=1173396371)

---

### Post by yabbadabbadont on 2007-03-08
It looks like you dual boot with windows.  If so, boot windows and change the drive label there.  (or at least verify that it *isn't* what is showing up in Ubuntu)

---

### Post by Chipmaster on 2007-03-08
I managed to rename it with mlabel, but it was a painfully long task and not all that n00b friendly.  I think the renaming of a partition (especially of a format that linux can read and write to) should be integrated into ubuntu and not require the downloading of extra tools or booting into a different operating system.  Just a suggestion to make this awesome OS even better :D

---

