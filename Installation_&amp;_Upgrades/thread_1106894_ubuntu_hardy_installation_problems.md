---
title: "ubuntu hardy installation problems"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by yajson on 2009-03-26
im installing ubuntu and after I reach the partioning portion there's a prompt that says
"before you select a new partition size, any previous changes have to be written to disk. you cannot undo this operation.
Please note that the resize operation may take a long time.

Go Back Continue


after i click continue there's a prompt again saying
"too small size"
ok

then after i click ok it will go back to the partioning portion again.

im dual booting xp and ubuntu and there's a 30 gb on my drive C 16.4G is still unused.

what do you think could be the problem?

---

### Post by Kevbert on 2009-03-26
Welcome to Ubuntu.
It may be that your trying to install to the small amount of free space at the end of the disk. If you have a free partition (which is formatted) use manual partitioning and delete this partition. Set a new partition for swap to twice your ram size (for paging and hibernation) and use the rest for the system. The system should be formatted to ext3 (the default linux format) and mounted /
If the Windows partition includes the spare space you'll need to shrink the partition to allow Ubuntu to be installed in it's own partition.

---

