---
title: "gparted can format anything BUT ext2/ext3"
date: 2009-09-08
forum: Hardware
---

### Post by daweefolk on 2009-09-08
I'm trying to format my external hd but at one point it crashed halfway through and since then I haven't been able to format it as anything linux related. ntfs, fat32, fat, even reiserfs, but none of the ext formats. seeing as i can't format it to a linux filesystem, fsck would have no effect, correct?
What else could I try?

---

### Post by ajgreeny on 2009-09-08
Were you using gparted?  If not try that and delete any partitions on the drive, if you are able to see any, then make a new partition and format that to your chosen system.  If that does not work, you may need to try something like dban, which will wipe the drive of any data and leave it totally empty.

---

### Post by louieb on 2009-09-08
Along the same line as ajgreeny - in Gparted - bring up the hard drive - then from the menu - Device> New disk label... 

Choose the default msdos disk label type. This will write a new blank partition table to the disk. Its a lot faster than dban and  if it does not work then you can always try dban next.

---

### Post by daweefolk on 2009-09-09
i set the partition table to msdos but still no ext formats. time for dban

---

