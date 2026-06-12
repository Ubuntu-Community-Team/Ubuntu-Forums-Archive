---
title: "correcting ntfs"
date: 2008-10-24
forum: General Help
---

### Post by yed79 on 2008-10-24
When trying to delete files on an ntfs partition I'm getting Input/Output error, which I googled to mean there's a problem in the partition (corrupted).
fsck seems to only work on unix partitions.

How to correct ntfs partition on ubuntu?

Thanks,
Yed

---

### Post by Sef on 2008-10-26
Moved to General Help.

Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk_Download").

---

### Post by bigbear2350 on 2008-10-27
NTFS dosent have any fsck tools on linux since NTFS is a trade secret.

To correct ntfs issues you have to run chkdsk on windows.

---

### Post by drs305 on 2008-10-27
NTFS problems are best solved via Windows. However, if windows is not available and you cannot solve the issue via other means, there is an option available from within linux. 

If you install **ntfsprogs** there is an app called **ntfsfix** that can solve some of the basic ntfs errors which might prevent mounting. Read about it via "**man ntfsfix**" before using it.

---

