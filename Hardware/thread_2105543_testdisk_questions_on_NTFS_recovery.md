---
title: "testdisk questions on NTFS recovery"
date: 2013-01-16
forum: Hardware
---

### Post by sdowney717 on 2013-01-16
I put a 2nd NTFS 200gb maxtor into a win7 pc and win7 wiped the drive? I heard it go on boot up, the arm running across the disk for about 3 seconds and now win7 and ubuntu gparted say the disk is unallocated space?

There was a full win7 install on that disk.

So now thinking to try testdisk on it.
And it found linux partitions??
So I clicked the linux partition and it shows a linux and then some NTFS partitions.
Testdisk is right now analyzing the cylinders.

SO what do I do when it is finished analyzing?
Am I on the right track or way off base?

---

### Post by tgalati4 on 2013-01-16
Let testdisk finish.  I doubt Win7 deleted your drive.  More likely, Win7 didn't know how to read a linux partition table, even though you have an NTFS partition on it with a Win7 install.

---

### Post by sdowney717 on 2013-01-16
testdisk could not fix the drive, said it was too small.

Then all it says it cant recover a fat 16 partition, what happened to all the others?
There is no fat 16 partition on the drive.

I am trying photorec on it.
It has found 65,000 txt files which are nothing but unreadable junk so far
And a few other things.
Can it recover any .doc files?
Who knows.

---

