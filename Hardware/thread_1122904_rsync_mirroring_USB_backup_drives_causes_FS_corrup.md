---
title: "rsync mirroring USB backup drives causes FS corruption"
date: 2009-04-11
forum: Hardware
---

### Post by jrowberg on 2009-04-11
I have recently setup two external 1TB USB drives (Western Digital Elements) in a poor man's RAID 1 setup for backup purposes.  Just to be clear, there is actually no RAID at all, but the functionality I'm looking for is similar.  I use one drive to store everything on, and then periodically rsync that drive onto the other drive, however, I'm having a problem with filesystem corruption, and as this is a BACKUP drive, I don't want to have to worry about that at all.

I'm currently running Jaunty Alpha6, i386 arch, if it makes a difference.  I don't think it does.  None of the filesystems are ext4, so the data loss bug with that system is not affecting this.  Both USB drives were formatted ext3.  Both are powered externally (not by the USB bus).  Both are plugged into an IOGEAR USB 2.0 4-port hub (which is not externally powered itself).  I have about 600GB of data currently on the primary 1TB drive, which is many hundreds of thousands of files--about 15 years of data archives from five people.

The problem is that when I tried the following command:

```
rsync -avz /media/Backup1TB-1/* /media/Backup1TB-2/
```

It hums along merrily for a long time--maybe 150GB or so worth of data--and then all of a sudden all of the rest of the source files "disappear" and no more data is copied.  Both drives remain mounted, and the destination drive contains good data--as much as was copied, anyway.  The source drive has some good data left, and all of the file and directory entries are still there, but many of them are displayed as "??????" when I run "ls" as root, and they just say "Stale NFS file handle" when I run "ls" as a regular user.  I can't access the data anymore.  I can unmount the drive, but attempting to remount it complains about a bad superblock.  fsck will (sometimes) run on the drive, but it finds all kinds of errors, wants to remove and recreate the journal, and after finishing up leaves me with a whole bunch of missing files.  This is obviously not acceptable.

I don't understand how this could possibly happen to the SOURCE DRIVE during an rsync operation that should only be reading data.  I tried this same process again twice, since I luckily still have the data on old drives, and all three times the same behavior occurred.  The last time, I tried making the destination drive a ReiserFS partition and then mounting the source drive as read-only before doing the rsync, and it completed successfully.  I attribute that more to the RO mount than the ReiserFS destination, but I'm not really sure.

So, in summary, a couple of questions that I would love to have answered:

1. Why the heck did that happen in the first place?
2. Is there a more preferable way to do what I'm trying to do?
3. Is ReiserFS more suitable for this kind of application?
4. Is a USB hub a bad idea here, even if the drives are externally powered?

Any help is appreciated.  I have all of my data at this point, but I'm walking on eggshells instead of feeling secure in having a simple mirrored backup solution.

---

