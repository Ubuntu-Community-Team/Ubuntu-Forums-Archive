---
title: "Just Copy Files to Do System Backup?"
date: 2008-08-16
forum: General Help
---

### Post by raywood on 2008-08-16
I want to make a backup of my Hardy installation.  I have an external USB drive.  Can I make a restorable backup by just copying all of the files in File System (using Nautilus) to a folder on that external drive?  I guess I would boot with a live CD to restore them all if the system failed.

---

### Post by pytheas22 on 2008-08-16
In principle it would work to just copy all of the files over somewhere, but there are better ways to do it, and things you should keep in mind that will make it easier to restore things later if necessary.  This [thread]("http://ubuntuforums.org/showthread.php?t=35087") is a good guide.

---

### Post by aheckler on 2008-08-16
You could just use rsync to backup your entire home directory. That works pretty well for me.

---

### Post by raywood on 2008-08-18
[thread]("http://ubuntuforums.org/showthread.php?t=35087") sounds a bit tentative, like Heliode was still working it out.  (See e.g., post 30.)  That thread is 65 pages long, so I didn't read the whole thing.

---

### Post by raywood on 2008-08-18
> **aheckler said:**
> You could just use rsync to backup your entire home directory.

Why back up only /home?  Shouldn't I back up everything on the partition?

---

