---
title: "fsck problems on system boot"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by tj111 on 2007-11-26
When ever I reboot my system, it drops to a shell giving me errors related to fsck on /dev/sda2. According to my partition editor this is an empty partition (used to have XP installed on it).  I formatted the partition as ext3 and also tried just leaving it as an empty partition, but it always gives me this error.  If I type "reboot" or hit ctrl+d, boot continues as normal and I have no problems while running Ubuntu.  Any help is appreciated.

/var/log/fsck/checkfs:
> 
Log of fsck -C -R -A -a 
Mon Nov 26 22:10:15 2007

fsck 1.40.2 (12-Jul-2007)
/dev/sda2: Superblock has an invalid ext3 journal (inode 8).
CLEARED.
*** ext3 journal has been deleted - filesystem is now ext2 only ***

/dev/sda2: Resize inode not valid.  

/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Mon Nov 26 22:10:15 2007
----------------

---

### Post by rsambuca on 2007-11-26
Do exactly what it says.  Run an fsck -f on the partition.

---

