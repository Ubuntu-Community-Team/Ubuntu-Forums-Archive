---
title: "After Installing windows 7 Ubuntu file system crashed"
date: 2010-04-22
forum: Hardware
---

### Post by Awadi on 2010-04-22
Hello all, I hope this is posted in the right section, I believe this is my first post.

Have HP nc6220 notebook, 100GB, 1GB. Had win xp and Ubuntu 9.04 using grub boot manager. I installed an image of win7 replacing win xp, works perfect, Grub menu works fine (nothing changed) but, when I select to boot Ubuntu I get all kind of error messages,

error message:

fsck 1.41.4 (27 jan  2009) 
/dev/sda3:clean, 53/48384 files, 63619/192780 blocks 
fsck.ext4: unable to resolve uuid=9b21f588-1be3-4517-9850-cf12a389e298 
fsck died with exit status 8

I booted livecd run fdisk -l::

ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 6
Warning: ignoring extra data in partition table 6
Warning: ignoring extra data in partition table 6
Warning: invalid flag 0xd735 of partition table 6 will be corrected by w(rite)

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4564    36658408+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4565       10517    47817472+   7  HPFS/NTFS
/dev/sda3           10518       10541      192780   83  Linux
/dev/sda4           10542       12161    13012619    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           10542       11514     7815591   83  Linux
/dev/sda6   ?      178941      211292   259858717   8e  Linux LVM


To make things worst, when I run GParted, I get just one block of unallocated (93.16GB), I can still mount linux and windows partitions and access files normaly in any file manager but there's nothing in /home :confused:

I've been using and learning Ubuntu for a year on several different installations but never seen anything like this. I never had trouble finding a post to resolve my Ubuntu issues and questions but, couldn't find anything relating to this problem unless I searched for the wrong thing.

Any help would be greatly appreciated, as this notebook is my daughter's only notebook and has all her files that I'm not sure if they're still there.

Thank you so much

---

### Post by P4man on 2010-04-22
First error message might be rather trivial. Looks like the UUID of the partition changed, you may just want to correct it in /etc/fstab. If you cant boot ubuntu anymore at all, then do so from a livecd. 

You can find the correct UUIDS by running

```
ls -l /dev/disk/by-uuid

```

Compare them to what is in /etc/fstab and change accordingly.

Not sure that will fix all your woes, but its probably a good first step.

---

### Post by Awadi on 2010-04-22
P4man, thanks for the reply, I tried the code you provided, the result shows all sdax's except for sda6 which is the home partition that has all the files.
From what I've been reading and what I what I got from "fdisk" that there's an overlap of partitions, here's what happened (but I still don't know how to reverse that or fix it);
The image I used is Acronis image and because the source partition was larger than the target partition (although the data is way less than the total size of the partition) Acronis did not warn about this instead it took messed up the partitions on the hard drive.

ubuntu@ubuntu:~$ sudo fdisk /dev/sda1

The number of cylinders for this disk is set to 4563.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Now I know what the problem is and how it happened but still don't have a solution for it


Partition 1 does not end on cylinder boundary.
Partition 2 does not end on cylinder boundary.
Warning: partition 1 overlaps partition 2.
Partition 3 does not end on cylinder boundary.
Warning: partition 1 overlaps partition 3.
Warning: partition 2 overlaps partition 3.
Partition 4 does not end on cylinder boundary.
Warning: partition 1 overlaps partition 4.
Total allocated sectors 1527228243 greater than the maximum 73316817



In short, we have an 6 overlapped partitions, I haven't made any changes since the problem started and, need to put them back in order and, I have NO clue what so ever on how to fix that. 

Any suggestions???

Right now I'm looking at "testdisk" which I never used and from what I read it can really ruin my drive if I don't know what I'm doing (and of course I don't)

Thanks again

---

### Post by Awadi on 2010-04-22
Solved.
Testdisk indicated there an error on the number of heads per cylinders and suggested it should be 255 instead of 240, corrected and written to MBR and voila  everything is back to normal.
Thanks to all of you and many thanks to Testdisk creator.
BTW I used Testdisk for windows on the same notebook, workded great.

---

