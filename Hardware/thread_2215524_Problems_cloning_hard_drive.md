---
title: "Problems cloning hard drive"
date: 2014-04-07
forum: Hardware
---

### Post by Aries01 on 2014-04-07
Hello. I have often successfully cloned the HDD with Ubuntu on it using the following command: sudo dd if=/dev/sda of=/dev/sdb. I recently tried it with a disk that has the 64 bit version of Ubuntu 13.10: when the command is being executed there is a message of a input/output error but that does not abort the process. Examination of the cloned disk with Disk Utility indicates that other partitions have been copied but not the ones used to run Ubuntu OS; Disk Utility also reports a bad sector in the source disk. Has the 64 bit OS been engineered to prevent this kind of cloning, or is the problem caused by the bad sector?

---

### Post by TheFu on 2014-04-07
bad sector, bad cable, failing disk controller. Not an issue related to being 64-bit. If you booted a 32-bit liveCD and tried the same thing, it would likely fail in the same place too.

Also, you might want to add a bs= to the command to speed this up 100x or use ddrescue which doesn't get confused by 1 tiny issue on a failing hdd.  RTFM carefully on ddrescue - it is the same, but different. ALWAYS use a LOG file with it.

Oh and cloning from a 512b sector HDD to a 4Kb sector HDD is better done with other tools. Important performance considerations.

---

### Post by sudodus on 2014-04-07
> **TheFu said:**
> bad sector, bad cable, failing disk controller. Not an issue related to being 64-bit. If you booted a 32-bit liveCD and tried the same thing, it would likely fail in the same place too.

Also, you might want to add a bs= to the command to speed this up 100x or use ddrescue which doesn't get confused by 1 tiny issue on a failing hdd.  RTFM carefully on ddrescue - it is the same, but different. ALWAYS use a LOG file with it.

Oh and cloning from a 512b sector HDD to a 4Kb sector HDD is better done with other tools. Important performance considerations.

+1

ddrescue can do much better than the original dd, when there are bad sectors or 'almost bad sectors'. The info page is better than the man page. See ```
info ddrescue
```

Clonezilla is more efficient than dd, and I think it works if there are bad sectors where there is no file (free space), but has problems too, if there is a bad sector where there is a data for a file.

---

### Post by TheFu on 2014-04-07
Last time I looked at **clonezilla**, it was too complex for my needs.  Discovered **partimage** which does a nice job ... but don't recall if it supports ext4 (with inside knowledge), I prefer NOT to have to reboot special just to backup partitions.  **fsarchiver** also does a nice job and compresses the output like clonezilla and partimage do (when they understand the file system).

Or ... you could use this opportunity to validate your backup AND restore process.  Everyone needs one of those - even if it is just an **rsync -avz**, it is better than nothing and much more efficient than dd. I prefer **rdiff-backup** myself, but there are lots and lots of backup tools that can be automated, are efficient with disk, network, time.  No backup on any of my systems takes longer than 5 minutes (I get a report daily) after the first backup is performed. It is pretty easy to have 60-90 days of backup data for the non-media files. I believe there are something like 30 different systems that I backup here. I've had to restore the entire email system for 3 companies after a failed upgrade once - took 45 minutes to restore after 15 minutes of trying to figure out if it could be corrected quicker - had to try, right? rdiff-backup rocks for my needs.

There really isn't any substitute for good, versioned, backups.

---

### Post by sudodus on 2014-04-07
I used PING for dual boot disks, and PING used partimage, but when I started using ext4, I had to find something else, and found Clonezilla that uses partclone instead of partimage. At that time partimage did not support ext4. I don't think it does now.

I listen to your advice, *TheFu*, in the general discussion about backup. If you need no complete clone (or cloned compressed image), there are many tools that are better (than the cloning tools).

---

