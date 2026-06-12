---
title: "Copying partitions from extended and primary partitions to LVM partitions"
date: 2008-10-01
forum: General Help
---

### Post by briandu on 2008-10-01
:confused:
Hi all,
my problems is this:
I want to move my existing partition setup and migrate it to a new disk (larger) with the same partition layout BUT the partitions are LVM except for the boot. [i,e each old partition corresponds to the new partition]
I have tried:
**partimage**  - stored image to 3rd disk and then found partimage generates a inode /dev/md error when I want to move files from 3rd disk to target disk - so it does not work.
**clonezilla** - does not support LVM so no go
**rsync** - this just partition overflows and I have tried various flag combos and it still partition overflows (seems to ignore the flags and follows links) 
**cp** - with various research flags - same result as rsync

The point is I want a "snapshot" on a larger disk so I can grow and support LVM snapshots.

I am about to do my nut.

Any ideas please? 

Ubuntu 8.10
2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

---

### Post by briandu on 2008-10-01
bump? anybody?

---

