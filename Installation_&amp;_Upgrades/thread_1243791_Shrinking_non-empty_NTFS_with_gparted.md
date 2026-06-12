---
title: "Shrinking non-empty NTFS with gparted?"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by billdotson on 2009-08-18
Hello, I have a PC running Windows Vista and one running Windows XP SP2. I have unused space on the NTFS partitions on each and want to shrink them so I have more room for installing Ubuntu. If there is already data on them will it destroy data to shrink them? These drives have been defragged. I have taken the Windows XP SP2 partition on other installs and enlarged it and I don't think I have had any filesystem errors other than Windows XP recognizing a change and wanting to run chkdsk on boot (which has passed both times I have tried this).

I use ntfsclone to image my Windows XP partition to a backup file that I compress with bzip2 so if I make a backup it has to be restored to the exact size (or very close size) on the same partition on the same hard drive to work (at least I think so) so if I think I may need the space later I had to go ahead and change the partition size. If I come back later and shrink it can I move my ext3 and other partitions up or will that cause damage (assuming they are unmounted)?

Thanks.

---

### Post by starcraft.man on 2009-08-18
Good of you to defrag first. The answer is no, you won't damage your ntfs partition just by shrinking it. Tho only way you'll damage the drive is if you have a failure of some sort during partitioning, unlikely. Good that you backed up the partition just in case.

I can't vouch for the clone program your using, but many imaging apps do supporting imaging back to a partition smaller than original. The absolute condition is that the partition must be strictly larger than the amount of data that was originally stored. So when shrinking, be sure to leave some space for buffer in the partition (i.e. if all the data takes up 20 GB, leave it at least 25).

The last question not sure I understand by move up? Once resized you can move the free space to wherever you want, be it merged into an existing partition or to another place on the disk with move to form a partition. No operation done by gparted in and of itself destroys data.

---

### Post by billdotson on 2009-08-19
I mean if I have a partition that starts at sector "x" and I want to move it so it starts at sector "y", closer to the first partition.

I am using ntfsclone, part of ntfsprogs and libntfs10. It works great for ntfs (as far as I know) as it is FREE (big plus for me) and instead of copying the empty data as zeros or whatever they would be with dd it uses a sparse file so the file isn't so big. I don't know how it works if you save to the special image format as it doesn't use the sparse file, but it still is only the size of the data that is on the partition (not "empty" space). Works for XP backups very well. Apparently Vista is made in some way that it will not boot (or you have to use a recovery cd or some nonsense) if it is cloned with anything as far as I know. Also, if you have partitions or it has been cloned you can't install service pack 2. I hate Microsoft.

---

### Post by raymondh on 2009-08-19
> **billdotson said:**
> I mean if I have a partition that starts at sector "x" and I want to move it so it starts at sector "y", closer to the first partition.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)

Back-up first ;)

---

