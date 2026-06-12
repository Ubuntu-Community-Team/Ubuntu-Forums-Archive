---
title: "[SOLVED] Amarok doesn't see shared partition"
date: 2008-09-01
forum: General Help
---

### Post by Artery on 2008-09-01
Hello, this is my first post, so you'll have to excuse me if I say anything particularly stupid.

I'm successfully dual booting XP and ubuntu.  My Drive setup is more or less 

205gb to windows, 10 ubuntu (EXT3) 14 Shared (NTFS) and then a 1GB swap partition in that order

I'm using the 14gb shared partition for files I want to be able to access on both drives.  The truth is I'm doing this VERY inefficiently mostly because I don't want to pull off all 50GB of media on my windows partition into a shared partition, and then share it, so for now, 14GB is plenty. 

In windows I transfered ~6gb of files into the shared partition, but when I try to add them in Amarok, it doesn't see the partition.  I'm looking in Settings-> configure amarok -> Collection

All I see is the directory beginning with "/" which as best I can tell is just the drive Ubuntu is on.  

My shared partition was mounted by default (i never had to mount it manually) and both windows and linux can see it in "explorer" (or whatever it is called in linux).  The shortcut for the shared partition does not appear under "desktop" when i look in amarok. 

Help?

---

### Post by drs305 on 2008-09-01
You mentioned "both drives". If one is an external drive use Amarok and browse to /media  The external is proably mounted on /media - so it might be something like /media/sdb2 or, if labeled, /media/my_music

You can also run "mount" to see where your partitons are mounted. Then use that information to navigate to the correct folder in Amarok.

---

### Post by Artery on 2008-09-01
Its actually one hard drive, but I followed your advice, and low and behold its under "media"

Thanks!

---

