---
title: "USB flash drive not updating free space"
date: 2008-11-07
forum: Hardware
---

### Post by IronFox on 2008-11-07
When I remove files from my flash drive, the free space wont update.  So when I try to put more files on it, it says there is not enough free space, even though theres more than enough.


EDIT:  Now that I play with it some more, when I dismounted the drive, it said something about a trash can for the flash drive.  When I emptied it, my free space came back.  Whats up with that?

---

### Post by enduser000 on 2009-02-19
> **IronFox said:**
> When I remove files from my flash drive, the free space wont update.  So when I try to put more files on it, it says there is not enough free space, even though theres more than enough.


EDIT:  Now that I play with it some more, when I dismounted the drive, it said something about a trash can for the flash drive.  When I emptied it, my free space came back.  Whats up with that?

I think the problem is that when you create the bootable flash drive using System->Administration->Create a USB startup disk it asks how much extra space you want to save your documents in or if you just want to discard them.  So you choose 1GB.  That means you have 1GB *already* allocated for space, if you save nothing, it's taking up 1GB on your flashdrive, if you save 1GB worth of information, it's taking up 1GB of information.  This is because it created the filesystem to which you save your documents when you create the bootable USB startu disk.

enduser

---

