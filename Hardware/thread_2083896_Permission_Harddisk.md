---
title: "Permission Harddisk"
date: 2012-11-13
forum: Hardware
---

### Post by babisayabundar on 2012-11-13
After I've installed PySDM Storage Device Manager, everything has changed.

The disk can mount at startup like I wanted, but the permission is changed. Now I can't Rename file or folder on that disk, I can't delete file or folder on that disk. And I have a folder on that disk before, named with Hangul / Korean Alphabet but now it shows "??".

Anyone can help?

---

### Post by gerowen on 2012-11-14
Is this a secondary disk that you just use for storage?  Since you mentioned it mounting at startup, I will assume so.  However, before continuing, ensure that the storage device manager software you are using does not require any special groups or user accounts to have permissions on the drive.  These are some generic instructions on how to set permissions on a folder or drive.

The "-R" flag in the following commands will apply these commands to the specified folder and all subfolders and their contents.  If you only wish to modify the folder specified, but not its subfolders, you can remove the "-R" flag.  Since it sounds like we're dealing with an external hard drive though that you want to do what you want with, I would leave it in.

Use the "chown" command to change ownership of files or folders.  For example to change the owner of an entire folder to yourself you would use:
```
sudo chown -R YOURUSERNAME /SOME/FOLDER
```

To change the owning group to your group you would run:
```
sudo chgrp -R YOURUSERNAME /SOME/FOLDER
```

To grant yourself and your group full permissions, and deny access to others you would run:
```
sudo chmod -R 770 /SOME/FOLDER
```

---

### Post by oldfred on 2012-11-14
The gui tools have not been updated for quite a while, so it really is better just to manually set your own entries. Is it Linux format or NTFS. You cannot reset permissions on NTFS as it does not support ownership nor permissions. You only have the defaults you set in fstab.

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
Also see this on how default permissions from fstab work
[http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259)

If a Linux formatted partition gerowen's commands will give more ownership & permissions but be sure to only run on data partitions. Recursively resetting anything in / (root) can destroy system.

I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod 775 /mnt/data
sudo chown $USER:$USER /mnt/data
#where $USER should be your login name

sudo chmod -R a+rwX,o-w /mnt/data
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

---

