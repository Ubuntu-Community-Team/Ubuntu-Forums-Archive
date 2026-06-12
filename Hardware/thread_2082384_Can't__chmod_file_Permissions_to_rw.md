---
title: "Can't  chmod file Permissions to rw"
date: 2012-11-09
forum: Hardware
---

### Post by Gregor Jordaan on 2012-11-09
What does it mean if I get a banner saying Permission denied after the command 
/dev/sdb2 /media/Macintosh_HD hfsplus rw,exec,auto,users 0 0 on a Mac OS Journalled external hard drive

---

### Post by Lars Noodén on 2012-11-09
Welcome.

Unless things have changed, journalling must be turned off to use HFS+ partitions with Linux.  You'll have to do that from OS X.  But then after that, you should have read-write access.

```

sudo /usr/sbin/diskutil disableJournal /Volumes/Foo

```

That's in OS X with the terminal. It can also be done graphically using Disk Utility.

---

