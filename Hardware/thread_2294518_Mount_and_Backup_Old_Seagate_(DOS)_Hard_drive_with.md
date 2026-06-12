---
title: "Mount and Backup Old Seagate (DOS) Hard drive with IDE adapter cable"
date: 2015-09-11
forum: Hardware
---

### Post by thatsmyboy on 2015-09-11
I have a 1620 MB hard drive (Seagate ST31621A) that runs DOS / Windows 3.11 that I would like to image and backup. 
```
lsusb
``` yields :

Bus 001 Device 010: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge

```
sudo fdisk -l
``` yields :
Disk /dev/sdb: 1623 MB, 1623690240 bytes
16 heads, 63 sectors/track, 3146 cylinders, total 3171270 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           9     3170159     1585075+  54  OnTrackDM6

From what I understand OnTrackDM6 is a disk manager that allowed BIOS on old systems to recognize hard drives larger than their maximum coded values (this is before 1GB hard drives were common). I also heard that you can boot to such a device by editing your grub bootloader :

from [http://ramses.smeyers.be/varia/OnTrackDM6/](http://ramses.smeyers.be/varia/OnTrackDM6/)
> Adapt your bootloader and add the option hd<x>=remap63 for your kernel where x is your disk.

Now reboot your system and the partition is visibale as (for example)

/dev/hdc1   *           1         826      832576+   6  FAT16

Mount this partition as read-only and copy your data from it


All I'm trying to do is get the data off the drive. Can anyone help me figure out how to mount it?

---

### Post by weatherman2 on 2015-09-11
Try the second answer here:

[http://superuser.com/questions/878591/mounting-an-old-dos-harddrive-on-linux](http://superuser.com/questions/878591/mounting-an-old-dos-harddrive-on-linux)

---

### Post by thatsmyboy on 2015-09-15
I have tried the sdb=remap63 option in the grub bootloader with no success (I was aware of the technique and mentioned it in my original post). Is there a way to mount with a fs -54 option or something? It is certainly recognized by fdisk. 
> Device Boot Start End Blocks **Id System**
/dev/sdb1 * 9 3170159 1585075+ **54 OnTrackDM6**
Any further help would be appreciated :p

EDIT: just for future reference, I did also see a note on connection order ( [seen here]("http://ubuntuforums.org/showthread.php?t=1102066&p=10315113#post10315113") )

    > This is the most ridiculous thing on the planet, but yes ORDER DOES MATTER!

and I followed the order they specified.

---

