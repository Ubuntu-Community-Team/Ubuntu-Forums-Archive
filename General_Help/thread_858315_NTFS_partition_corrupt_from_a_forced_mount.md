---
title: "NTFS partition corrupt from a forced mount"
date: 2008-07-13
forum: General Help
---

### Post by iperez13 on 2008-07-13
After I installed Ubuntu on my primary disk, I attempted to mount my secondary disk (single NTFS partition).  It said it was already in use somehow (I had no idea how since I had just booted up), so it couldn't mount it.

Clicking on Details showed a tip that you could force the mount, so I tried that, but after mounting it gave some warnings and then there was no data listed on the disk.

I have over 300gb of data on this disk, so I re-installed Windows in an attempt to fix the problem with various disk recovery software.  In Windows, the partition shows as RAW (which I assume means it doesn't know what it is).  I ended up trying Test Disk ([http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")) and was pleasantly surprised to see that it found my partition and was able to rewrite the partition table.  It could even list the files/directories on the disk just fine.

After it re-wrote the partition table, it told me I needed to restart, which I did.  After the restart, however, the problem remained.

So this is where I am now.  I am posting here in hopes that someone else has experienced this problem and has found a solution.  I still don't understand how Test Disk shows that I have a valid partition and it can even list the files, but yet Windows and Ubuntu both think that there is nothing on the drive.

Any help in this matter is greatly appreciated.

Thanks,
Ian

---

### Post by PmDematagoda on 2008-07-13
Did you try using tools such as ntfsfix or ntfsclone to try and recover the NTFS partition?

---

### Post by ianrobertperez on 2008-07-13
> **PmDematagoda said:**
> Did you try using tools such as ntfsfix or ntfsclone to try and recover the NTFS partition?

No, I didn't try that.  However, I am beginning to think my partition is corrupt for another reason.  I had windows installed before I installed Ubuntu, and the last time I shutdown I got an error that said something like "delayed write failed to D:\$Mft", which I assume means it didn't finish writing its changes to the master file table, thus resulting in its corruption.

I am now using the recovery utility called GetDataBack for NTFS to restore the data, and it is working well.

Thanks for the help

---

