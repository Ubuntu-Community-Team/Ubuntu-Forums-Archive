---
title: "Problems writing to my MP3 Player"
date: 2006-02-09
forum: Hardware &amp; Laptops
---

### Post by tc10b on 2006-02-09
Hi I'm a complete newb with Linux but I'm trying to learn.

I've got a Packard Bell Audiotwin and when I plug it in Ubuntu recognises it and can read and play from it. However when I try to write to it, it always says that there isn't enough space available, even when it's blank! :confused: 

I'm wondering if this is a driver problem or not as it seems to be able to read it fine.
It is displayed as the following in device manager

SigmaTel MSCN Music Player: MP3 PLAYER

Can anyone help me to get it to write files from my hard drive?

---

### Post by aysiu on 2006-02-09
I've heard of permission being denied but not running out of disk space...

Can you plug the player in, go to Applications > Accessories > Terminal, and then post here the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by tc10b on 2006-02-09
tc10b@tc10b-175-227:~$ sudo fdisk -l
Password:

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1909    15334011   83  Linux
/dev/hda2            3496        3648     1228972+   5  Extended
/dev/hda5            3496        3648     1228941   82  Linux swap / Solaris

Disk /dev/sda: 255 MB, 255066112 bytes
139 heads, 56 sectors/track, 64 cylinders
Units = cylinders of 7784 * 512 = 3985408 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          64      249060    b  W95 FAT32
tc10b@tc10b-175-227:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              15G  2.2G   12G  16% /
tmpfs                 252M     0  252M   0% /dev/shm
tmpfs                 252M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
/dev/hdc              2.2G  2.2G     0 100% /media/cdrom0
/dev/sda1             243M  242M  942K 100% /media/MP3 PLAYER
tc10b@tc10b-175-227:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
tc10b@tc10b-175-227:~$

I know that the disk has more room than the 942K. Could it be because it is FAT32?

---

### Post by Zimmer on 2006-02-09
Have you deleted stuff from it before?  If you have you will have probably created hidden trash folders. Check the properties option to view hidden files and see what is there. If there are hidden trash folders delete them.....

---

### Post by tc10b on 2006-02-10
Cheers that worked! Thanks

How do I stop it from creating a trash folder so I can just delete stuff easily?

---

### Post by Zimmer on 2006-02-10
[QUOTE=tc10b]Cheers that worked! Thanks

How do I stop it from creating a trash folder so I can just delete stuff easily?[/QUOTE]
try in Nautilus going to  
Edit>Preferences and the tab Behaviour
There is an option to put a delete command into Nautilus options that bypasses the Trash can...a simple tick in the box :)

---

### Post by ollyshaw on 2006-02-13
I have used that Zimmer,
 
However pressing delete still moves files to trash, can i get the delete button to simply wipe the file?

Thanks

Olly

---

### Post by Zimmer on 2006-02-13
Are you sure? I have just tested that on a file on my MP3 player/USB stick and the file was NOT moved to a trash folder, just deleted. 
In the preferences I have both Trash options ticked, one to ask me before deleting and the other ticked to put the Delete option on the menu that bypasses Trash...I then use Delete, NOT 'Move to Trash'.
It does however create 'empty' hidden trash folders. I have no problem with  empty folders... they can be deleted too, or left alone, as they will certainly reappear at the next delete operation.

---

