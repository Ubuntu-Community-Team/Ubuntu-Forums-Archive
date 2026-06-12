---
title: "USB Hard-drive recovery?"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by gen0 on 2006-11-21
I could use some suggestions on a problem I've got.

I have a laptop with an external 3.5" IDE drive in a USB enclosure.  This external drive has started giving me problems, and now I can't access one of the NTFS partitions (in windows or linux).  I can mount it, but get the following error when I try to get a directory listing:

ls: reading directory ntfs: Input/output error

In dmesg, I get this line of output:

[17187057.820000] NTFS-fs error (device sdb5): ntfs_readdir(): Directory index record with vcn 0x3 is corrupt.  Corrupt inode 0x5.  Run chkdsk.


I've tried to use various disk-imaging programs to try to back-up/recover this partition (ntfsclone, partimage, device-image), but all of them seem to fail when they encounter bad reads on the hard-drive - apparently because the USB driver disconnects the drive when there errors happen.  (The devices disappear from the filesystem under /dev/sdb*, and dmesg output fills up with:

[17186726.008000]  27:0:0:0: rejecting I/O to dead device


Has anyone got any suggestions as to what I could do to recover this partition?

---

### Post by teaker1s on 2006-11-26
plug it into an xp machine and run check disc-failing that look at hard disk makers website for diagnostic and recovery tools-that's how I fixed a buggered xp box

---

