---
title: "Format Problem"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by Demosthenes on 2005-06-19
Hi, firstly I'd like to say that although this is my first post I have been using these forums for some time and I find them to be a most excellent resource full of knowledgeable and helpful people.

Recently I purchased a new hard drive for data storage and envisaging that I may want to access this data in both linux and windows I formatted the drive as FAT32 using gparted.  After formatting the drive was reported as FAT32 and I could use it as such, so I began filling the drive up and thought nothing more of it.  However upon my next boot into Windows (about a month or so later) I found the disk was not detected and that Partition Magic reports the drive as ext2.  This seems to me rather odd since the disk works perfectly in Ubuntu as a FAT32 drive.

Also I have formatted a friends external usb drive like this and he has encountered the same problem on his XP machine.

If anyone can shed any light on the problem here it would be appreciated, although I hardly ever use Windows any more (thanks to Ubuntu) I would like to get to the bottom of this issue.

---

### Post by xy77 on 2005-06-21
When the hdd is mounted on ubuntu, check the output of
```

$ mount

```
whether ext2 of vfat is stated behind the device.

Greetings,
  David (xy77)

---

### Post by Demosthenes on 2005-06-21
The output of mount list vfat after the device.

---

### Post by xy77 on 2005-06-22
what does
```

$ fdisk -l /dev/sdxn

```
(where x is the number of scsi/usb-disk and n the partition number) say?

It may be, that the partition table (FAT) is set to ext2, but it was formated as fat32. Maybe this confuses Win.

Greetings,
  David (xy77)

---

### Post by Demosthenes on 2005-06-22
The device is IDE rather than scsi/usb but the result is:
```
$ fdisk -l /dev/hda1

Disk /dev/hda1: 300.0 GB, 300066407424 bytes
255 heads, 63 sectors/track, 36480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System
```

And:

```
$ fdisk -l /dev/hda

Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       36481   293033601   83  Linux

```

---

### Post by xy77 on 2005-06-22
[QUOTE=Demosthenes]The device is IDE rather than scsi/usb but the result is:
```
$ fdisk -l /dev/hda1

Disk /dev/hda1: 300.0 GB, 300066407424 bytes
255 heads, 63 sectors/track, 36480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System
```
[/QUOTE]
Pretty huge hdd :-) I made a mistake, it should be
```

$ fdisk -l /dev/hda

```
without the partition number, to see the general setup of the hdd.

[QUOTE=Demosthenes]
```
$ fdisk -l /dev/hda

Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       36481   293033601   83  Linux

```[/QUOTE]

This one seems to be the problem. The "System" is Linux, partition table id #83. I suppose Window's will not further invesigate a partition marked Linux, although on filesystem base, it's fat32. If you don't mind losing the data, you could use fdisk or cfdisk (more convenient) to set the partition type to Windows Fat32 something (there are a few types, I don't know which one is best suited). after that you **could** end up, having windows and linux recognize the partition, but don't blame me if you lost your precious data.

Greetings,
  David (xy77)

---

### Post by Demosthenes on 2005-06-22
I think I shall just have to survive as I currently am until I have the chance, time and inclination to back up all the data that resides on that drive, before I try something like that.  In future I shall not use gparted to make fat32 drives.

Thanks for your help anyway.

---

