---
title: "Uninstallation foul-up"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by anotherposter on 2009-11-04
I needed to remove Ubuntu from a dual-boot machine (really needed the 10Gb of space for windows, only had Ubuntu on that machine for testing).

However I seem to have ended up with a windows installation that is completely confused about the size of the disk and partition.

Both the disk and the only partition are 40G, but windows now thinks there's only 30.

Grub is gone (did fixmbr thing).  Ubuntu paritions are deleted.  If I run Ubuntu live disk and partition editor it says the whole disk is NTFS already.  It also, weirdly, says its all empty, which it isn't.

If I run XP boot disk repair mode and diskpartition command it tells me I have a single 40G NTFS partition (same thing Ubuntu boot disk says).  Checkdisk says its fine.

Basically everything says I have a single 40G Windows partition, except windows itself which insists there's only 30G.  If you check disk properties in windows itself it says the partition is 40G but the total space is 30G, contradicting itself.

How do I get the other 10G back?  I _really_ can't face reformatting and reinstalling and downloading 1 million windows updates.

I even tried reinstalling Ubuntu so I could then try and delete it again, but it just gave a weird error message and refused to continue at the partition setting stage.

This is sort of a windows problem now, but it started with Ubuntu, so maybe someone else has had this issue?

---

### Post by dstew on 2009-11-04
I recall something like this. If you increase the partition size, that is not enough. You also need to increase the *file system* size. With command-line tools, there are two steps. I am trying to remember where I learned this. It was while I was trying to rescue a Windows system partition table, using Linux tools. I was able to do it, but I remember this problem.

Its coming back to me slowly. I resized a NTFS partition using gparted, but the file system was still small. I used the [ntfsresize]("http://man.linux-ntfs.org/ntfsresize.8.html") program to increase the file system to fill the partition. I think this program is on the gparted live CD (use the command-line).

---

### Post by anotherposter on 2009-11-05
Thanks very much!  I followed your suggestion and it worked perfectly.  Learned something new here, didn't know about the file system size thing, was convinced the partition info was screwed up beyond salvation.  Thanks again - Googling had failed to turn up any information on this problem.

---

