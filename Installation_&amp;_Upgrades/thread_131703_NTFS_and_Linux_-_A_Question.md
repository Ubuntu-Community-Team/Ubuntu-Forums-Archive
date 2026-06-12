---
title: "NTFS and Linux - A Question"
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by Rev. Nathan on 2006-02-16
I want to clean out my Windows partition and shrink it down, giving me more space for Linux. Can I do this for free somehow? Maybe delete all I need in Windows and use _________ partition manager in Windows to shrink the NTFS partition? Also, could I somehow actively swap data from Windows to Linux? As in, move my 40GB of music that is on my Windows partition to my Linux partition, and not have to worry about freeing up space?

Thanks for any help and insight --

BTW XFS or ResierFS? I'm using Reiser... can anyone give me a quicklist to positives and negatives of each?

---

### Post by alfonz on 2006-02-17
if all you are looking for is to use the music files just to play then you can mount the windows partition and play the files from there. That way you don't need to use up more space.

use this [guide]("http://easylinux.info/wiki/Ubuntu") to help you mount  your windows partitions.

---

### Post by Rev. Nathan on 2006-02-17
I've been doing that. My intention is to completely nix Windows, and carry over all my old documents onto Linux, without a third party (such as an extra hard drive). Then, expand my Linux partition, and reinstall/reformat Windows to a smaller partition, [and enabling Fat32 for easier filesharing? Or is that a little unsafe in the world of Windows? Or is it even possible with XP?].

---

### Post by montablac on 2006-02-17
yea,what he said,but be carefull,if you try and wright to the NTFS partition,youll couript it and all the data in it

if your not using winNT/ME/XP try using a FAT partition for windows

---

### Post by kenweill on 2006-02-17
You can expand the Linux partition from Windows.
I've been using Partition Magic. From Windows, I can easily transfer any files from windows to linux, and vice versa without any problem at all.
Only, Partition Magic is not free.

---

### Post by aysiu on 2006-02-17
[DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142) is free, as long as you have a broadband connection and a CD burner.

You can also use Knoppix (which has QTParted).

---

### Post by az on 2006-02-17
[QUOTE=Rev. Nathan]
BTW XFS or ResierFS? I'm using Reiser... can anyone give me a quicklist to positives and negatives of each?[/QUOTE]
The free-libre partitoining tools (parted ntfstools) will properly do the job.  There is no need to Partition Magic.

Why is Ext3 not an option?  ReiserFs is faster when dealing with millions of small files.  If you are running a server with a tremendous load, you will appreciate the difference.  On a desktop, forget it.  I don't know what the advantages of XFS are, only that you will not see any of the benefit when runnning a desktop system.

I beleive that Ext3 is more stable and reliable than Reiser and XFS on linux.

---

