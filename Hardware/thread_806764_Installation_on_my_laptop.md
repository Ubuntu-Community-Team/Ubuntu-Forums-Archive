---
title: "Installation on my laptop"
date: 2008-05-25
forum: Hardware
---

### Post by ubockto on 2008-05-25
ok, my laptop, currently lying defunct due a catastrophic error on my behalf, was running its OEM XP, I know it will install Ubuntu 8.04, but what I want to know, will this be able to leave the files on there, plus install as a NTFS file system, or will it install as the default Ubuntu file system?

---

### Post by Marat Galiev on 2008-05-25
You must install Ubuntu on ext3 or reiserfs file systems.

---

### Post by spiritfox on 2008-05-25
Although you do have to install Ubuntu on these filesystems, what I believe you can do (My most recent install was about 6 months ago, so I could be wrong) is create a new partition without destroying your old NTFS one.  This could be a fairly small partition and would not neccessarily need to serve as anything more than a rescue mission to back up your old files, which would be accessible (but not writeable) from the Ubuntu partition.

---

### Post by #Reistlehr- on 2008-05-25
If your NTFS partition is not 100% filled, you can download and install gparted or use the resize partition feature in the ubuntu install (I think alternative is the only one that allows you to resize, but i can be wrong). Then create a new parition with the free space. You can make the parition a minimum of 4 gigs. i think the smallest is 3, but 4 is for the extra software you'll want to install. It will not touch your NTFS files. you can download the ntfs-3g drivers (sudo apt-get install ntfs-3g) and then when you mount a NTFS drive, it will be readable/writable. I think this behaviour is default in Hardy.

---

### Post by ubockto on 2008-05-25
But will it leave the NTFS partition intact, and will it be readable by Ubuntu?

---

### Post by Zimmer on 2008-05-25
> **ubockto said:**
> But will it leave the NTFS partition intact, and will it be readable by Ubuntu?

If you wish to just rescue your Winxp files (ie your personal data) before attempting to install Ubuntu ( I guess you have no way of re installing XP?) then I suggest you use a live cd to access the NTFS partition and copy the files you want to external media.

---

