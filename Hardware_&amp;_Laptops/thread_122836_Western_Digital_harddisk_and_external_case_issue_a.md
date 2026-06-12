---
title: "Western Digital harddisk and external case issue and (possible) solution"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by BjornW on 2006-01-28
Just a quick hint to spare others from the agony of finding out why the [Western Digital]("http://www.wdc.com/") 200GB hardddisk won't show up when you use it in a [Digiconnect]("http://www.digiconnect.nl") USB2.0 (HD360) external case. 

Before else make sure the harddisk works and partion it as you see fit. The easiest way is to install the harddisk in a computer as a slave and partition it with your favorite tool. I partioned it using [gParted]("http://gparted.sourceforge.net"), as one big disk in [FAT32]("http://support.microsoft.com/support/kb/articles/q154/9/97.asp") for the best compatibility with the different operating systems (Linux, OS X and Windows 98/2000/XP). If the disk is ready to use, mount the disk and if the disk is mounted try to see if you can write files and read files to it. If this works the disk is ok.

Now make **REALLY** sure the jumpers on the back of the Western Digital are removed. So don't set the Master/Slave settings explicitly. Now you'll be able to use the HD in the case and it will be automagically mounted (OS X 10.4 and Ubuntu 5.10 Breezy Badger). If you don't remove the jumpers the drive won't mount or even show up in any logs and you won't have a clue what the problem is, because you've set the jumpers as you would do always. Highly annoying!

Remove the jumpers and problem solved. Tested it with OS X 10.4 and Ubuntu Breezy Badger :mrgreen:

---

