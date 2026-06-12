---
title: "[SOLVED] Hard drive permissions"
date: 2008-08-17
forum: General Help
---

### Post by bravo sierra echo on 2008-08-17
Linux newbie here, so please assume I don't know anything!

I was given a spare 3.5inch hard drive and have mounted it internally, planning to use for extra storage if I ever fill my main drive.  It mounts fine, and I deleted everything off it.  However, I can't write anything to it - it says I don't have permission.  When I try to alter the permissions from the properties menu, it tells me the permissions could not be determined.

Maybe there's a command line method of changing the permissions?

Any help appreciated!

---

### Post by drs305 on 2008-08-17
This guidance is for ext3 formats. 
The command to change the ownership to you and group to your group is:
```

sudo chown -R ***yourusername:*** ***/mountpoint***

```

An example, username=dave, mountpoint= /media/storage
```

sudo chown -R ***dave:*** ***/media/storage***

```

The command to change permissions (rwx to owner, read/write to group and others):
```

sudo chmod -R 755 ***/mountpoint***

```

Added: I mentioned ext3 partitions because ntfs and vfat partitions set the ownership at mounting.

---

### Post by bravo sierra echo on 2008-08-17
That's done it.  Fantastic, thanks very much indeed!

---

### Post by sisco311 on 2008-08-17
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

