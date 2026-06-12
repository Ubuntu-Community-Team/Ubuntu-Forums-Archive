---
title: "FileSystem Advice"
date: 2008-07-13
forum: General Help
---

### Post by henrypootel on 2008-07-13
Hi
I've just finally changing my home PC completely over to Ubuntu Hardy, with a small XP partition for the games that just don't work in WINE(Mass Effect in particular).
I have 2 data drives(containing Music, photos etc..)which are NTFS formatted, and i'm starting to get annoyed at how i have to mount these all the time to access them from Hardy. What i want to know is:
-is there a way to get them automatically mounted? and
-should i change the filesystem on these drives? I still want to be able to see them from XP, but this is quite rare, so a small amount of hassle is fine if there are benefits in doing so.

---

### Post by Taxman415a on 2008-07-13
To get them automatically mounted you just need to get your /etc/fstab file setup properly. See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)   for that. Be careful, and make sure to back up your fstab (cp /etc/fstab /etc/fstab.old for example)

You can access files on an ext3 filesystem from XP by installing an ext2 driver in XP. It can then read ext2 and ext3 partitions. So you can make ext3 your new data storage filesystem. The problem will be that in order to change filesystems on a drive you need to reformat it. So to save your data you'll have to back it all up somewhere else and then restore it.

The downside of not switching filesystems is that you may potentially corrupt the data you have on the ntfs filesystems by writing to them from linux. The drivers are much better now than they used to be, but they aren't foolproof.

---

