---
title: "Strange error in installation?"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by RavenOfOdin on 2006-01-28
OK, I've gotten the install to the point where I can make swap and root (/) partition on my drive. The other drives for Windows are pre-set as /media/hda1 and /media/hda2.

In attempted installation, I receive this:

> 
System~1_Resto~1RP920CHANGE~1.1 is 1k, but it has 4 clusters (16k)

Error!!!

    <Ignore>
    <Cancel>

<Go back>


I've done some checking into this problem and other related threads. Since I don't want to wipe the drive clean. . . my only two options are to gauge whether or not its OK to ignore this file, or re-make the partitions. I haven't tried re-making them yet, but I've gone through both Chkdsk and Seagate diagnostics. This drive is a Seagate ST380020A, and as near as I can tell, its not going bad yet.

Seagate Diagnostics returned a result of "Invalid file size" on drive D: with only 1 error. Chkdsk didn't return anything.

Is there anything I can do, or am I screwed?

---

### Post by RavenOfOdin on 2006-01-28
PS: Apparently the error checking utility from within Windows "ScanDisk" corrected the invalid file's size from 658 bytes to 16,384. Everything's OK now.

(EDIT: 'Tis now done. And GRUB hasn't caused one problem whatsoever. :D )

---

