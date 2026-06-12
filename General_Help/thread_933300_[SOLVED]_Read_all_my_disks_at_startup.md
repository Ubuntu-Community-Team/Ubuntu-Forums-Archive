---
title: "[SOLVED] Read all my disks at startup"
date: 2008-09-29
forum: General Help
---

### Post by kokkus on 2008-09-29
Hi.
When I startup my ubuhntu, I have to go to Desktop and then to my other hdd to let ubuntu read from it.
So is it possible to let ubuntu read from it from startup?
And when I enable the hdd, it comes up on my desktop, is it possible to turn that function off so my hhd, ftp's and stuff will not show up on the desktop?

Thanks:)

---

### Post by Elfy on 2008-09-29
The hardrive isn't in fstab I expect, is it ntfs/ext3 or something else. CAn you run this from a terminal and post the outputs please

```
cat /etc/fstab
sudo fdisk -l
```

To stop hdds showing on the desktop you can mount them in /mnt rather than /media - if you want none to show on the desktop then ALt+F2 and run gconf-editor - navigate to
apps/nautilus/desktop and disable volumes_visible

Downloads showing on the desktop are being put there by the browser - change the download destination

---

### Post by kokkus on 2008-09-29
Thanks. Ok here's the output:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1032646e-50c3-426a-8dff-e8ad2dca4d97 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=bf57a4c6-ab45-46d5-af65-8547ad857c87 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0

---

### Post by Elfy on 2008-09-29
can you post the result of both codes please

---

### Post by kokkus on 2008-09-29
OH sorry I forgot fdisk -l

[sudo] password for chris: 

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44d344d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30514   245103673+   7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d595ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29288   235255828+  83  Linux
/dev/sdb2           29289       30515     9855877+   5  Extended
/dev/sdb5           29289       30515     9855846   82  Linux swap / Solaris

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9de9d64e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801    c  W95 FAT32 (LBA)

---

### Post by Elfy on 2008-09-29
The way to get the partitions to mount on boot is to add them to fstab, for the ntfs it is possible to install ntfs-config which puts a tool in the system tool menu which acn be used, but as you're going to be editing the fstab file anyway just as easy to add them there.

To allow them to mount you need to have a folder available either in /media or /mnt.

This thread goes through adding an ext3 partition to fstab
[http://ubuntuforums.org/showpost.php?p=5720510&postcount=5](http://ubuntuforums.org/showpost.php?p=5720510&postcount=5)
This is bodhizazens fstab - comprehensive :) [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Check both and you should be able to see how to get the ntfs and fat32 drive mounted.

Hope that is a help - come back if you need more

---

### Post by kokkus on 2008-09-29
But I don't understand a bit of this pc geek stuff, so I suppose I should let it be as it is now when it still works:)
All I wonted to fix it so Ubuntu could read the other disk too when I start ubuntu so I don't have to click on the disk icon every time, but ok thank you anyway:)

Edit: I tried the program you told me to install, but even when I enabled it it won't read the disk when I start ubuntu.
I still have to click on it from the places menu to let Ubuntu read it.

I mean, the /disk folder won't come up under /media before I click on the 251,0GB disk icon on the places menu.
And my music is on that disk so I have to always click on that icon to let my music player read the music files.

---

### Post by Elfy on 2008-09-29
ok well that's fine - neither did I last year.

If you want to do it then make 2 folders 

```
sudo mkdir /media/ntfs /media/fat32
```

Backup and open fstab for editing

```
sudo cp /etc/fstab /etc/fstab.2909
gksudo gedit /etc/fstab
```

And add these 2 lines to the end of the file

```
/dev/sdc1 /media/fat32 vfat defaults,user,dmask=027,fmask=137 0 0
/dev/sda1 /media/ntfs ntfs-3g defaults,locale=en_US.utf8 0 0
```

Should do it for you.

---

### Post by kokkus on 2008-09-29
Wow it works!!!
THanks alot :)

---

