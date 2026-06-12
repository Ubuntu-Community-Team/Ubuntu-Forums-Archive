---
title: "Help me find my second hard drive please."
date: 2009-06-22
forum: Hardware
---

### Post by Mr.Internaitonal on 2009-06-22
I just installed Ubuntu 9.04 today, everything went good, execpt i could not find my second hard drive. However, i found a link for the hard drive in filesystem/dev/disk/, but when I try to open it it says: No application is known for this kind of file. Please help me!! :(

---

### Post by louieb on 2009-06-22
To see whats drives and partitions are on your computer 
Open Applications>accessories>terminal and run
```
sudo fdisk -l
``` lowercase L at the end
Enter your password when asked
Please paste the output in your next post

---

### Post by Mr.Internaitonal on 2009-06-22
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22609697

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6994    56179273+  83  Linux
/dev/sda2            6995        7297     2433847+   5  Extended
/dev/sda5            6995        7297     2433816   82  Linux swap / Solaris

my second drive is 500gb, i think these are all partitions

---

### Post by wanderingarticfox on 2009-06-22
Quite a few pages to read but look up my day old thread "Installed 9.04 and lost Windows Hdd in GRUB" it is in the installations category and then go to the 3rd page and you will find the info for SUPER GRUB; it solved my problem which turned out that the mount point was not on the 'edge' of the disc/sector. I'm new to this too but that SGD is awesome. :D

---

### Post by Mr.Internaitonal on 2009-06-22
thanks for trying to help me wanderingarticfox, but i am trying to get my stuff from my second drive, not trying to boot windows

---

### Post by louieb on 2009-06-23
fdisk shows just 1 60GB hard drive with Linux installed and using the whole drive. 

Is the 2nd drive internal or external?

If internal is it sata or ide (aka pata)?  Power off, open it up and check the connections. Sata will only plug in one way. 

If IDE (wide flat ribbon cable) make sure the colored wire is next to the power plug. 

If still no 2nd drive check BIOS setup to see if its detected. 

BTW once the 2nd drive is detected its partitons will show up in the places menu.  Ubuntu wil access (mount) it in the /media folder. 

Just a word of warning: the /dev directory is special (defines block devices) it should not normally  be used to access data directly.

---

### Post by Mr.Internaitonal on 2009-06-23
My second drive is internal sata, im sure it is connected because in windows vista it showed up


It didnt show up in bios
but i checked and it is connected right.

---

### Post by louieb on 2009-06-24
Sure seems like a hardware problem. Can't think of any other reason to not see the drive at all. If you can't see the drive in BIOS - then Ubuntu and the fdisk program are not going to be able to see or access it.

Try another cable. Try plugging it in to a different port on the mother board. Check to see if its getting power - can you hear it spinning up when you turn it on?   Pull it out and stick it in a USB enclosure or another PC.

Really can't think of much else to pin down why.

---

### Post by wanderingarticfox on 2009-06-24
My Windows is on a different drive than my Ubuntu; the Super GRUB located the drive so I could access it. Accessing the drive was the issue; Windows just has some data I needed/wanted to config. 9.04.

---

### Post by Therion on 2009-06-24
Simple question, but I don't see it being asked...  Is the drive showing under your "Places" menu?

---

### Post by Mr.Internaitonal on 2009-06-24
Nope

---

### Post by wanderingarticfox on 2009-06-25
[SIZE="3"]Super Grub solved the problem; it was a 'mount point' issue and Super Grub picked it up.[/SIZE]
  Going for a Sept. '09 build of 9.04 AMD64 alternate install for a RAID 1  so I can install a 9.04 x.86_32 guest of 9.04 on the 'software RAID'.
  I want to fire MS>><<<< I am learning to Ubutnu :D

---

### Post by wanderingarticfox on 2009-06-25
SOLUTION:
 SUPER Grub picked up the OEM mount point and now things are fine.

  Anyone with similar dual boot dual HDD should try SUPERGRUB as a possible solution:D

---

### Post by wanderingarticfox on 2009-06-25
Like I already said; I have 2 drives; Windows was not 'detected' SUPERGRUB found the 'mount_point' on that drive. I was not looking for "windows' I was looking for the Drive>>>Super GRUB did IT; no argument no doupt; try it >>it is open source and powerful and will do no harm<<<<<<<<<<<< if not then give up!!!!!!!!!!!!!!!

---

### Post by wanderingarticfox on 2009-06-25
Try SUPERGRUB!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Divider on 2009-06-25
try this one.

```
sudo cat /proc/partitions
```

---

### Post by pbpersson on 2009-06-25
You can install gparted and then go to System-->Administration-->Partition Editor however I don't think that would give you a different result than the fdisk -l command that you did at the terminal prompt.

---

