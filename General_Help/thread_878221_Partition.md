---
title: "Partition"
date: 2008-08-02
forum: General Help
---

### Post by ProgenitorVirus on 2008-08-02
For some reason, I have my HDD set up like this:

/dev/sda1 ntfs 227.38 GB
unallocated 5.50 GB
/dev/sda2 extended 232.88 GB
unallocated 5.51 GB
/dev/sda5 ext3 224.48 GB
/dev/sda6 linux swap 2.90 GB

Okay, the problem is I have two different parts for my unallocated space, and I need it to be only one.

Can't figure out how to fix this.

Any help is great!

Thanks!

---

### Post by PurposeOfReason on 2008-08-02
What you'd have to do is delete move sda2 to the left and combine the two unallocated space. If they can't be moved, delete them and make them free space but I think that's the same thing.

---

### Post by mikewhatever on 2008-08-02
Yeah, use gparted live cd to eliminate the unneeded unallocated space.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

