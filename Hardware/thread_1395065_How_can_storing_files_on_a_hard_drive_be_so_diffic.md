---
title: "How can storing files on a hard drive be so difficult?"
date: 2010-01-31
forum: Hardware
---

### Post by AmericanAussie on 2010-01-31
New to Ubuntu...I've tried everything I can find to solve this problem, but I have to admit defeat.  I have two internal hard drives, installed Ubuntu alongside WinXP, then cleared the WinXP drive and partitioned it to ext3.

Nothing I do allows me to access the drive to store files on it.  I've spent at least 20 hours over the last 3 days searching the forum, reading the documentation, etc.  I've tried duplicating an entry of a working, accessible hard drive (where my home directory lives) in fstab, using the appropriate UUID...all that does is cause the drive to no longer appear on the Places menu.

Is there ANY simple way to enable me to store files (like .odt word processing files) on this hard drive?  Right now it's totally useless, might as well not even be there.  System security is a wonderful thing, but this is a little ridiculous.

Any help?

---

### Post by milton1 on 2010-01-31
what are the permissions on the drives mount point?

---

### Post by AmericanAussie on 2010-01-31
Right-clicking the desktop icon after mounting, selecting Properties, then selecting the Permissions tab gives me:  The permissions of "Storage 1" could not be determined.

---

### Post by Morbius1 on 2010-01-31
When you reformatted the partition to ext3 it became an extension the the root file system. You can verify that by running the following command from the Terminal:

**ls -dl "/media/Storgage 1"**

It should come back with something that looks like this:

drwxr-xr-x # [COLOR=Blue]root root[/COLOR]

If it does then you need to take possession of the mount point:

Open **Terminal**
Type **sudo chown morbius:morbius "/media/Storage 1"**

Change morbius to your user name

---

### Post by AmericanAussie on 2010-01-31
Well, I managed to gain the access I wanted using chown.  I guess I'll have to re-partition the disk and practice using chown and chmod.  Thanks for the help.

---

