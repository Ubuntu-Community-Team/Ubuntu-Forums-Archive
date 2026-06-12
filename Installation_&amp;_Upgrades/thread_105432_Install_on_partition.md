---
title: "Install on partition?"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-12-18
I have a 20 GB disk where I have made a 3 GB partition. But when I run the installation CD I can only choose to delete the whole disk. I have tried to select the manual partitioning but have no idea about what I should choose.

How do I install Ubuntu on the 3GB partition and leave the rest of the disk intact??

---

### Post by az on 2005-12-18
[QUOTE=bigblop]I have a 20 GB disk where I have made a 3 GB partition. But when I run the installation CD I can only choose to delete the whole disk. I have tried to select the manual partitioning but have no idea about what I should choose.

How do I install Ubuntu on the 3GB partition and leave the rest of the disk intact??[/QUOTE]

If the installer does not give you the option to use the free space, it is because it cannot use it - probably because it was not made successfully or properly.  What did you use to make the partition?  The fact that it does not offer to free up some space for you is not a sign that the partition table is healthy.

You can probably try to delete the partition and leave it as free space.  The installer will default to offering using the free space.

---

### Post by roelofs on 2005-12-28
> If the installer does not give you the option to use the free space, it is because it cannot use it - probably because it was not made successfully or properly.

That may be the case some of the time, but it seems clear there's a bug in Debian/Ubuntu's partman, too.  When other Linux distros can mount such partitions, and specific components such as fdisk, mke2fs, and e2fsck can manipulate them without trouble, it's pretty hard to believe that it's the fault of the disk or its partition table.

> You can probably try to delete the partition and leave it as free space. The installer will default to offering using the free space.

Speaking only for myself, that does not (did not) work.  If the partitions in question are logical ones inside an extended partition, and if Ubuntu can't see inside the extended partition in the first place, then deleting/resizing/formatting the logical drives is irrelevant--and, when some of the logical drives have useful information on them, deleting the whole extended partition is...unpalatable, to say the least. :(

Does Ubuntu have a bug-tracking system somewhere?

---

### Post by psusi on 2005-12-28
[http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com)

What does the output of fdisk -l show?

I think this problem might happen if the extended partition in question is type 0x0f ( w95 extended ).  If that is the case, try changing it to 5 ( extended ) with fdisk.

---

### Post by roelofs on 2006-01-04
> What does the output of fdisk -l show?

I think this problem might happen if the extended partition in question is type 0x0f ( w95 extended ). If that is the case, try changing it to 5 ( extended ) with fdisk.

You can see both "normal" fdisk output (actually lightly edited) and "expert" fdisk output on my [LinuxQuestions posting]("http://www.linuxquestions.org/questions/showthread.php?threadid=349241").  In short, it was indeed a "W95 Extended" partition, and no, changing the type label to 5 didn't help.  I think there's something about the format itself that partman doesn't like.

It looks like [bug 15795]("http://bugzilla.ubuntu.com/show_bug.cgi?id=15795") is probably the same thing; interestingly enough, it also involves a Maxtor disk.  Unfortunately, there have been no replies (other than mine just now) since it was posted in September. :-(

But thanks...hopefully this info will help someone else down the road.

---

