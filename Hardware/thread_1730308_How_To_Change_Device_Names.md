---
title: "How To Change Device Names?"
date: 2011-04-15
forum: Hardware
---

### Post by dniMretsaM on 2011-04-15
How do you change device (external HDD, USB flash drive, etc) names in Ubuntu? I know his is possible, but I can't figure out how. I've done some searching, but no answers. Any help would be greatly appreciated.

---

### Post by cymbaline42 on 2011-04-15
Depends on what kind of partition it is. 

ext2/ext3 partitions can be renamed using ***e2label*** ([http://linux.die.net/man/8/e2label](http://linux.die.net/man/8/e2label))

Fat32 partitions can be renamed using ***mtools ***([http://embraceubuntu.com/2006/03/01/editing-fat32-partition-labels-using-mtools/)]("http://embraceubuntu.com/2006/03/01/editing-fat32-partition-labels-using-mtools/")

Hope this helped.  Good luck.

---

### Post by dniMretsaM on 2011-04-16
Thanks. How about NTFS?

---

### Post by dniMretsaM on 2011-04-18
Bump.

---

### Post by cymbaline42 on 2011-04-23
I'm not entirely sure about NTFS.  A quick internet search yielded this, you might want to see if it works for you: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

