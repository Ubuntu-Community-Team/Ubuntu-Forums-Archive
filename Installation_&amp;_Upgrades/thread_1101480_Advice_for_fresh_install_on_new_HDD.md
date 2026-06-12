---
title: "Advice for fresh install on new HDD"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by elhauk on 2009-03-20
Hi
My computer currently runs with Ubuntu and XP on separate HDDs each of about 200 GB. Both disks are currently more or less full with photos, music and films.

The XP HDD is NFTS formated and is used for photos and music while the Ubuntu HDD is fat32. and stores films.

This setup was done when i first started testing Ubuntu.

As i have found i less and less use XP (but still need it for some work related programs) i am thinking of doing a fresh install of both XP and Ubuntu. I recently got a new HDD which i intend to use for the OS and let the two HDD consist of media.
I also would like to have everything ext3 formatted (except for the xp partition)

What is the best ways to do this?
I'm thinking of something like this:

HDD 1:
Partition 1 - NFTS - 15 GB - Windows installation
Partition 2 - SWAP - 5 GB (for 4 GB RAM)
Partition 3 - ext3 - 5 GB - /
Partition 4 - ext3 - 5 GB - /usr
Partition 5 - ext3 - the rest of the disk - /home

HDD 2 and 3:
whole disk - ext3 - can i have these as /home as well?

How about the size allocations on HDD 1? are they OK? Is 15 GB for XP too much? I'm intending to install ext3 support in XP so the 15 GB is only for OS and software. Don't think my current XP install takes that much space but thinking its smart to have some leeway.

---

### Post by dstew on 2009-03-20
I think overall your plan is sound. 15 Gb is fine for XP, I think. However, you can't have two /home partitions on one system. Remember, the mount point is a directory name on the file system, and there will be only one /home mount point. You will not be able to mount two devices to one mount point at the same time. To use the other disk on the same system you would have to create another mount point, like /storage, and mount it to that.

I think you might also be able to create a logical volume out of multiple partitions on multiple disks, and mount that to /home. See [this How-To]("https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall"). There is some information there about moving your /home to a logical volume.

---

### Post by tom56 on 2009-03-20
I wouldn't use separate partitions for /, /usr and /home. It's just too difficult to guess the right sizes for each. There's no benefit anyway, it's no substitute for regular backups.

---

### Post by elhauk on 2009-03-20
Could i call one hdd mountpoint /videos? or would i have to call it /home/username/Vieos to acces it from the places menu?

LVM is slightly advanced for me at the time being.

---

### Post by tom56 on 2009-03-20
> **elhauk said:**
> Could i call one hdd mountpoint /videos? or would i have to call it /home/username/Vieos to acces it from the places menu?

You can add any folder (regardless of where it is) to the Places menu by opening the folder in the file browser, then clicking "Bookmarks - > Add Bookmark".

---

