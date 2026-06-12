---
title: "Strange problem with Hardy... Acessing from XP"
date: 2008-10-25
forum: General Help
---

### Post by Sonolin on 2008-10-25
I just recently got a new hard drive, and instantly started to go to work at partitioning and installing a dual boot system for XP and Ubuntu.  I had previously used only Gutsy (7.10 I believe) which served me well, but I figured I'd upgrade to the new version (Hardy).  My partitioning scheme is basically 1 15gb partition for each OS (Hardy and Windows XP), a 200gb storage partition (ext3), and swap.  

The storage partition can be written to, read, etc. from both Ubuntu and XP.  I have used fs-drive on XP to read/write to ext2.  However, I CANNOT for the life of me get damn Windows XP to read OR write to any file at all that was made from Ubuntu with chown privileges of "sonolin" (my login).  If the file is made with root privileges, I can read/write to that file.  Otherwise, no.

The strange thing is is that I CAN read/write to any file on my old Gutsy installation from Windows XP.  

Windows will not even let me open a folder made with "sonolin's" privileges.  (I mount the storage partition to /home on Hardy.. not sure if this is a problem.. and cannot access the sonolin folder in /home at all.)

When accessing a file, fs-drive pops up this error:

"Z:\sonolin is not accessible.

The file or directory is corrupted and unreadable."



Any help you can give I would be very greatful, if this cannot be solved I guess I'll just reinstall Gutsy instead of Hardy.. but I really don't want to do that :(.  I do not even know how this is happening, because, according to fs-drive, it does not recognize permissions.

And it is not just fs-drive's fault.. I have tried ext2fsd to no avail.  No error but I cannot access any files made under sonolin as the owner.

---

### Post by Pro-reason on 2008-10-25
That's weird.  I use those drivers, and I've never had that problem.

Try using “fsck” to check that ext3 drive.

You could also make a new partition for those files which you think you may need from XP.  I personally have two storage partitions: one is ext3 (accessible from either system) and one is JFS (accessible only from Linux).  The latter has stuff like source code and .deb archives that I'm unlikely to need to access from Windows.

You could have a FAT32 partition and an ext3 partition.

---

