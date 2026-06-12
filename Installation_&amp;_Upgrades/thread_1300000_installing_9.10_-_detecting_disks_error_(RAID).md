---
title: "installing 9.10 - detecting disks error (RAID)"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by kamil212 on 2009-10-24
Trying to install 9.10 from the 64bit alternate CD and keep getting a partition disk error right after the drive detection. 
I get a screen:
> Detect Disks
One or more drives containing Serial ATA RAID configurations have been found. Do you want to activate these RAID devices?
Activate Serial ATA RAID devices?   YES/NO
No matter what I choose I get the Starting up Partitioner screen and a Partition Disk error:
> Could not stat device /dev/mapper/asr_AppArray - No such file or directory. 
ERROR!!!
Retry/Cancel
I had XP running on the RAID0 array but I killed the array right before trying to install. The Intel Matrix Storage Manager shows no RAID Disks, just 3 physical drives. 2 Seagates and 1 Maxtor.
When I select "nodmraid" option in the first ubuntu boot screen I get the same serial ata raid detection screen and it goes all the way to the partitioner but it doesn't detect my 2 seagates. 
Any help would be appreciated. 
(Trying to do the software RAID0 system drive)

---

### Post by kamil212 on 2009-10-24
anybody?
could the 32bit version have different drive support?

---

### Post by tomh0665 on 2009-10-25
Can you activate dmraid in a/another console and then detect your disks again?

---

### Post by kamil212 on 2009-10-25
Thanks, I gave up. 
This was my second attempt to get RAID working on Ubuntu with no success. (tried 2 years ago). 

Just did a basic install and now I'm going to try to reconnect my 2 Seagates and try to set up a RAID0 drive where I can work on my big files.

---

