---
title: "Help with extundelete"
date: 2015-05-08
forum: Hardware
---

### Post by andybuckle on 2015-05-08
A colleague had a synology external enclosure with 2 disks in RAID1. The device disconnected from the domain unexpectedly, possibly due to an issue with some DNS servers.

When he attempted to reconnect it, it did a reset deleting all data. I had removed the disks and built an ubuntu system to try to get some of it back. It's ext4. 

"extundelete --restore-all" got perhaps 5% of the data back, is there any chance that the other options for extundelete, (specifying block number and so on) will find any more?

I am also running photorec as I type, but then its tricky to figure out what's what due to the loss of filenames and directory names.

---

### Post by sudodus on 2015-05-08
Welcome to the Ubuntu Forums :-)

The first step would be to clone the wiped drive, and work on the cloned copy. I saw in another thread, that you have used ***ddrescue*** before - and I recommend using it again :-)

You might have some luck with ***testdisk*** to get the previous file system back. Otherwise there is the hard and messy work with ***photorec***. If you ***have to*** get back some files, that is the last resort, and it is likely to work, when everything else fails.

---

### Post by andybuckle on 2015-05-08
the disks are fine. so, I don't think ddrescue is needed. I need to undelete. testdisk says "Undelete files from FAT, exFAT, NTFS and ext2 filesystem". As I have ext4 here, I though extundelete was more appropriate.

finding stuff in the pile produced by photorec can be a pain...

---

### Post by dino99 on 2015-05-08
ext3/ext4 can be considered as ext2 here

---

### Post by sudodus on 2015-05-08
> **dino99 said:**
> ext3/ext4 can be considered as ext2 here

+1

---

