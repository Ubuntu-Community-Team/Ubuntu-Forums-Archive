---
title: "NAS disk format for mixed OS backups"
date: 2008-12-29
forum: Hardware
---

### Post by ggordon on 2008-12-29
I have two Ubuntu, two Windows XP, and one Vista system on a network that I need to backup.  I am considering getting a NAS drive for this purpose so that each system can write its own backups to the shared drive.

I'm wondering what would be the best format to use for the drive.  I think I remember reading that fat32 and ntfs cannot store all of the file ownership and permission information for Linux files unless they are first archived in a tar file.  I would prefer not to use tar.  But Windows is not compatible with ext3 is it?

I would prefer to have a single partition so as to have flexibility in how much space each system uses in the future.

Is there a single format that will work for all of the systems, or am I better off creating separate partitions for use by the Windows and Ubuntu systems?

---

### Post by albinootje on 2008-12-29
> **ggordon said:**
> I have two Ubuntu, two Windows XP, and one Vista system on a network that I need to backup.  I am considering getting a NAS drive for this purpose so that each system can write its own backups to the shared drive.

I have no experience with NAS-drives, but I wonder whether you have much choice concerning the various file-systems you can format it with.

What is the problem with tar ? 
There's also zip and rar for Linux in case you'd like that better.
There's also the p7zip GUI in MS-Windows which can do more than just p7zip alone.

There's software for MS-Windows which works with ext2 (and ext3) partitions, but I don't know whether that would work over a network.

---

### Post by wmoore on 2008-12-29
The disk format of the NAS is irrelevant as you are not accessing the partition directly*. More important is the network layer the NAS supports. Most will support Windows SMB, which you can access from Linux using Samba client. Otherwise look for a NAS with NFS support for native Linux access.


* Though having said that, you should probably format it as NTFS to keep your Windows happy, and allow you to store large backup files.

---

