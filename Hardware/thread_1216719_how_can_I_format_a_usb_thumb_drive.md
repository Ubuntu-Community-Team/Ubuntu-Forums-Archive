---
title: "how can I format a usb thumb drive?"
date: 2009-07-18
forum: Hardware
---

### Post by RobertL on 2009-07-18
On ubuntu 9.04 desktop I'm trying to use a Kingston "Data Traveler" 4GB thumb drive to store data. I'm not trying to boot from it (yet). I was planning to format it with a ext2 filesystem but fdisk doesn't seem to see it. Here's what I get:

sudo fdisk /dev/sdd
Unable to open /dev/sdd

I'm sure that's a valid device name because it appears when I insert the usb drive and disappears when I remove it. However, many other device names also appear and disappear when it is inserted or removed. 14 in all. They are: cdrom2, cdrom3, cdrw2, cdrw3, dvd2, dvd3, scd2, sdd, sg5, sg6, sr2, usbdev1.X_ep00, usbdev1.X_ep02, usbdev1.X_ep81. In the last three the 'X' increases by 1 each time the device is removed and then re-inserted. Do I need to get rid of these other devices before I can format sdd?  What is the significance of a single physical device having so many /dev entries?

True, this thumb drive is described as a "Secure privacy" drive and it has windows software on it intended to require a password before you can read or write on it. So it's probably intentionally rigged to prevent exactly what i'm trying to do. But there must be some way to wipe everything out and reformat it. How can I do that?

I examined it closely for a write-protect switch but there isn't one.

When I insert it, it automatically mounts read-only. The entry for it in /etc/mtab is:

/dev/sr2 /media/DTSP\040Launcher iso9660 ro,nosuid,nodev,uhelper=hal,uid=1000,utf8 0 0

---

### Post by ajgreeny on 2009-07-18
Boot into the ubuntu live CD, plug in the drive and open gparted, System >Administration >Partition Editor.  You should be able to see the drive in the drop down box top right, but make sure you get the right one.  Make sure all the partitions on it are unmounted (right click and choose unmount) then delete all the partitions on it and then make a new ext3 (why ext2?) partition.

---

### Post by Marlonsm on 2009-07-18
Insstall Gnome Partition Editor (GParted), you can find it in Applications > Add/Remove.

-Open it (will be inside System > Administration).
-Make sure to select the pendrive, usually your HD will be selected by default. To do so, change it on the top right part of the window.
-Right click the bar in the middle on the window, go to Format to...
-There you'll need to select the filesystem you want, usually FAT32 is the way to go.

---

### Post by PixelLord on 2009-07-18
Try this here:
[http://manpages.ubuntu.com/manpages/karmic/man8/mkfs.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/mkfs.8.html)

---

### Post by RobertL on 2009-07-18
> **ajgreeny said:**
> Boot into the ubuntu live CD, plug in the drive and open gparted, System >Administration >Partition Editor.  You should be able to see the drive in the drop down box top right, but make sure you get the right one.  Make sure all the partitions on it are unmounted (right click and choose unmount) then delete all the partitions on it and then make a new ext3 (why ext2?) partition.

The reason I said ext2 is that I understand usb thumb drives have a shorter life than hard drives because they gradually degrade every time they are written. Of course they can be written thousands of times, or tens of thousands, but they eventually "wear out". The journaling feature of ext3 causes many more writes to occur and thus shortens the life of the device for little benefit.

I'll try the methods given for formatting the thing but I would still like to get answers to the specific questions I asked if anybody knows.

---

### Post by RobertL on 2009-07-18
> **PixelLord said:**
> Try this here:
[http://manpages.ubuntu.com/manpages/karmic/man8/mkfs.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/mkfs.8.html)

That's basically what I already tried. As I say in the original posting, mkfs says it can't open the device.

---

### Post by RobertL on 2009-07-18
> **Marlonsm said:**
> Insstall Gnome Partition Editor (GParted), you can find it in Applications > Add/Remove.

-Open it (will be inside System > Administration).
-Make sure to select the pendrive, usually your HD will be selected by default. To do so, change it on the top right part of the window.
-Right click the bar in the middle on the window, go to Format to...
-There you'll need to select the filesystem you want, usually FAT32 is the way to go.

Thanks for the suggestion but GParted doesn't see the device. And yes I selected 'refresh devices'. It sees all the other disks but not the thumb drive. I tried it with the device mounted and not mounted -- same result.

---

### Post by RobertL on 2009-07-18
> **ajgreeny said:**
> Boot into the ubuntu live CD, plug in the drive and open gparted, System >Administration >Partition Editor.  You should be able to see the drive in the drop down box top right, but make sure you get the right one.  Make sure all the partitions on it are unmounted (right click and choose unmount) then delete all the partitions on it and then make a new ext3 (why ext2?) partition.

I know about partition editor but it doesn't see the device. Even after I click on 'refresh devices' and no matter whether it is mounted or not mounted. 

Yet I can write and read it under windows XP so I know it isn't broken.

---

### Post by DownTown22 on 2009-07-18
> **RobertL said:**
> I know about partition editor but it doesn't see the device. Even after I click on 'refresh devices' and no matter whether it is mounted or not mounted. 

Yet I can write and read it under windows XP so I know it isn't broken.

Why not format it under XP, thus removing any software that came on it.  You can format it to FAT or NTFS, then plug in into Ubuntu and reformat it via GParted to ext2.

---

### Post by RobertL on 2009-07-18
> **DownTown22 said:**
> Why not format it under XP, thus removing any software that came on it.  You can format it to FAT or NTFS, then plug in into Ubuntu and reformat it via GParted to ext2.

That's a good idea but I just tried it and unfortunately it doesn't help. I can format it on windows and write and read it fine but it still can't be seen on linux.  

I note that on windows, when the device is plugged in, an application pops up asking for a password, and this still happens even after I reformatted it. Also, after reformatting it still appears to be a 4-GB disk and also a 6.66 MB CD drive.  

I now see that the CD portion of the device contains the software that pops up (configured to auto-play).

Maybe there's something unique about the hardware in this thing and the autoplay software is a windows driver for it. There is also a folder on the "CD" portion with a lot of .dlls in it and at least one .sys file.

It's really frustrating and I've spent (wasted?) so much time on it. I don't want to accept the fact that I can't wipe it clean but maybe I can't. If no new ideas come up I guess I'll give up and it will just have to remain a mystery.

---

### Post by DownTown22 on 2009-07-18
Does Kingston have their own software to format those drives?

---

