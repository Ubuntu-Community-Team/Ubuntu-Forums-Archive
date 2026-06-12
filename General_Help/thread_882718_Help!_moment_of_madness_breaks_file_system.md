---
title: "Help! moment of madness breaks file system"
date: 2008-08-07
forum: General Help
---

### Post by martal on 2008-08-07
I have done something really stupid. I used a partition manager (Paragon) in XP to resize my Kubuntu home partition (smaller) and another bigger).

Now Kubuntu won't start.

/dev/sda9 resize inode not valid, UNEXPECTED INCONSISTENCY

run fsck manually

Can someone explain how to do this, also how to check which partitions need to be unmounted, and how to unmount?

---

### Post by matthurne on 2008-08-07
Hehe.

I mean, "oh man, I'm so sorry!"  :-)

What filesystem is on your Kubuntu partition?  It may be resizeable.  However, I believe the way you're supposed to do this is:

1) Resize filesystem
2) Resize partition

Rather than

1) Resize parition
2) Resize filesystem

The latter is what you'll be trying to do, but it may very well be the case that you've already trampled on the filesystem's contents by shrinking the partition.

Not sure I can offer much more than that - good luck to you!

---

### Post by ajgreeny on 2008-08-07
Youcan run fsck using the live CD.  Open a terminal and command ```
sudo e2fsck /dev/sda9
```though you may want to check that the live CD also sees that partition as sda9 first with ```
sudo fdisk -l
```
It is also worth checking that the UUID of the partition is not changed with ```
sudo blkid
```and then editing your installed version's fstab file if necessary.

---

### Post by martal on 2008-08-27
Hello guys, sorry about the delay in replying.

I just went ahead and reinstalled. Serves me right.

---

