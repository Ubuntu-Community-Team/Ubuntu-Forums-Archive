---
title: "Mtab Fstab drives"
date: 2008-09-15
forum: General Help
---

### Post by VoyeurOne on 2008-09-15
Ok I done did it. Took windows off my computer, reformatted all the partitions that weren't Linux to ext3 , took out the ntfs3g info from fstab and now when I start nautilus all my original linux drives show up in the left window but none of my newly formatted drives show up.   I can go to /media and use the drives / read/write but I can't figure out how to make them show in Nautilus.

I upgraded from Feisty to gutsy and to Hardy around the same time I did all of this , I am thinking that all them critters wrote a little in mtab and fstab. It also seems that my drives get renamed on every boot.

Is there a way to force Hardy to rescan the media and write a new mtab and fstab file, set a permanent mount point?

---

