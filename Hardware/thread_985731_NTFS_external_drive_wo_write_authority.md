---
title: "NTFS external drive w/o write authority"
date: 2008-11-17
forum: Hardware
---

### Post by khmorse76 on 2008-11-17
I have a Toshiba laptop with herron (Xubuntu) on it and a pair of external hard drives for my wife's photo collection.  These hard drives are formatted NTFS from when we had XP.  I can freely read the files, but cannot move or delete them.  Strange thing is that it only started a couple days ago.  The week prior we haven't had any problems.

I need to be able to write/delete on these NTFS hard drives.  Neither of us want to move back to Windows.  She's not technically savvy, but she enjoys the stability and speed of her 3 year old 'new' laptop.

---

### Post by cariboo on 2008-11-17
Use ntfsprogs to fix the permission problems on your extrenal NTFS drives. 

From Synaptic:
> tools for doing neat things in NTFS partitions from Linux
The Linux-NTFS project ([http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)) aims to bring full
support for the NTFS filesystem to the Linux operating system.

This is a set of tools targeted for people interested in working
with the NTFS support in the Linux kernel and using it.  The
following utilities are included:

ntfsfix - Fix common filesystem errors and force Windows to check NTFS.

mkntfs - Format a partition with an NTFS filesystem, optionally bootable.

ntfsinfo - Show some information about an NTFS partition or one of the
files or directories within it.

ntfslabel - Show, or set, an NTFS partition's volume label.

ntfsresize - Resize an NTFS partition without losing data.

ntfsundelete - Recover deleted files from an NTFS partition.

ntfscluster - Locate the owner of any given sector or cluster on an NTFS
partition.

ntfscat - Concatenate files and print them on the standard output
(without mounting the partition).

ntfsls - List directory contents on an NTFS filesystem (without
mounting).

ntfscp - Overwrite files on an NTFS partition.

ntfsclone - Efficiently clone an NTFS filesystem or a part of it.

ntfsmount - Mount an NTFS partition from user-space using libntfs and FUSE.

ntfsdecrypt - Decrypt NTFS-encrypted files (NOT INCLUDED).

ntfscmp - Compare two NTFS volumes and tell the differences.

Canonical provides critical updates for ntfsprogs until May 2010.

Ntfsprogs can be installed using Add/Remove Programs, SYnaptic Package Manager and of course the command line.

Jim

---

### Post by khmorse76 on 2008-11-18
Thanks, I'll check it out

---

### Post by alcapone-g on 2008-11-20
I had the same problem when I upgraded ubuntu 8.041 to ubuntu 8.10.
I think there is some bug in one of updates. My problem is even wears . I can only write from linux to NTFS drive only once then when I tried to copy files from NTFS under window Xp It crashes my external drive the way that I can not mount it on linux and as well I can not get access on win XP.

I got some suggestion about forcing mount, or try to get back to windows and do proper shut down. Non of these options worked. The access to drive was ruined. On win Xp I got message severe drive damage. On linux nothing worked.
 Finally I used from command prompt chkdsk command with f sweach in recovery mode to fix it. It did work I got back my harddisk with my files. Each time I accessed my drive from linux and wrote to it I had to fix it again. I quit using ubuntu 8.10 I went back to 8.041 and I do not have the problem anymore.

---

