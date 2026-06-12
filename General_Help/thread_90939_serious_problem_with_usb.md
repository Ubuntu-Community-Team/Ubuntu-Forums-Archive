---
title: "serious problem with usb"
date: 2005-11-16
forum: General Help
---

### Post by much better on 2005-11-16
Hi .. I have an external harddrive throuh usb and it devided into 5 partions .. The problem is that breezy can't mount more than 4 of them and in some cases just 3 and even just one .
What is the problem with breezy and how to fix it ?

---

### Post by hw-tph on 2005-11-16
Give us some more information. To start with, post the relevant log output from when you plug in the disk. Also post the output from **sudo fdisk -l** when the disk is inserted.


H&#229;kan

---

### Post by much better on 2005-11-16
[QUOTE=hw-tph]post the relevant log output from when you plug in the disk -l[/b]

[/QUOTE]




I didn't understand this step but here is the output of sudo fdisk -l :
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1        8001    1  FAT12
/dev/sda2               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/sda5               2        1276    10241406    b  W95 FAT32
/dev/sda6            1277        4580    26539348+   b  W95 FAT32
/dev/sda7            4581        7563    23960916    b  W95 FAT32
/dev/sda8            7564        9729    17398363+   b  W95 FAT32

---

### Post by much better on 2005-11-17
up .. where is everybody ?

---

### Post by the_it on 2005-11-17
If this is the usb disk you use most often, you can mount a particular partition using 
```
sudo mount /dev/sda# /mnt
```
where you replace sda# with the partition number you want to mount and /mnt with the place where you want to mount it (/mnt is usually okay for temporarily attached filesystems).

you'll probably want to mount sda5, sda6, sda7 and sda8, since these appear to be the actual partitions of your disk.

Don't forget to unmount the partition you are using with *sudo umount /mnt* before taking the disk out.

---

### Post by much better on 2005-11-19
You are great guys thanks alot , but how can i make the partion mounted automaticly ?

---

### Post by much better on 2005-11-20
up

---

### Post by the_it on 2005-11-20
[QUOTE=much better]You are great guys thanks alot , but how can i make the partion mounted automaticly ?[/QUOTE]

Ubuntu has automount behavior that I am not completely familiar with, so I usually turn it off.  There are a few things I can advise you, though, if you're okay with using the mount command

1) read the man page of pmount using *man pmount*
OR
2) statically allocate your fstab by creating entries that point to specific partitions of your usb disk

creating an fstab entry is easy.  It's commented fairly easy enough to understand.  You would probably add these lines to the fstab, and create a few directories in the /media directory.  However, take note that this is static allocation, so it will probably be iffy with usb disks that don't have the same partitioning scheme.

example line to add:
/dev/sda1 /media/sda1 auto defaults,users 0 0
/dev/sda2 /media/sda2 auto defaults,users 0 0
/dev/sda3 /media/sda3 auto defaults,users 0 0
/dev/sda4 /media/sda4 auto defaults,users 0 0

if you plan to use this scheme or something similar, open your fstab using sudo vi /etc/fstab and add lines like this, then sudo mkdir /media/sda#, from 1 to four.

Like I said I'm not really familiar with the automounting tools of gnome yet, so this is probably a lazy solution.

---

