---
title: "Uninstall Question"
date: 2008-09-17
forum: General Help
---

### Post by LevBeriv on 2008-09-17
Hello All,

I install a ubuntu build for a client and now they want it removed (long story). I put in my XP boot disk to preform a fresh install of XP and it does not see any partitions and does not let me format the disk because it thinks nothing is there. 

When I formatted for ubuntu with ubuntu disk I obviously changed the disk format. Is there a app that I can run from boot and get the disk back to NTFS?

I hope this is not a repost as I have searched quite extensive

-Lev

---

### Post by EmanresuusernamE on 2008-09-17
Right-click on My Computer, choose Manage.  Goto Disk Storage.  There will be a partition on one of the drives that says Unknown, (Healthy).  Delete that, and then create a new NTFS partition.

If you told XP to use the entire disk, then it should have already removed the Linux partition.

---

### Post by LevBeriv on 2008-09-17
I cannot click My COmputer windows does not exist -- ie one partition and ubuntu is on it

However I think I found my solution: [http://ubuntuforums.org/showthread.php?t=922376](http://ubuntuforums.org/showthread.php?t=922376)

---

### Post by EmanresuusernamE on 2008-09-17
Ohhh, my bad.  Jumped ahead of myself.  Put the hard drive in another windows box, then manage and repartition and reformat the drive. :)

Or load up Ubuntu, use gparted and then delete all of the partitions and format to NTFS.

---

