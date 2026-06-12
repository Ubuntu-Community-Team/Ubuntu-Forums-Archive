---
title: "new laptop and installing multiple distros?"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by dougleduck on 2009-02-07
I'm due to be getting a new laptop in couple of days. I want to try a few distros besides ubuntu for fun, :P. Itll have 320GB HD (slightly bigger than my current 20GB) so loads of room.

Itll have vista installed on it already, which I might leave for now.

From reading seems like the best bet for partitioning is something like

~ 20GB windows
15GB / for Ubuntu
20GB /home
~250MB /boot/grub
2GB swap
separate /media 

Is this sensible setup that should make it easier to add more distros?

---

### Post by Shazaam on 2009-02-07
Since it is a new laptop (still under warranty) I would suggest using a virtual environment to run multiple distros. It shouldn't void your warranty. Any app will work such as VMware, VirtualBox, etc. The only drawback is that 3d compatibility is still quite lacking in a virtual machine (games, Compiz, etc).
If you do go the partitioning route there are a few things you need to remember...
1. Use Vista's partitioner to make/change the Vista partition(s).
2. Make sure you have a "Restore" or full Vista install disk.
3. DON'T delete the Vista Restore/Recovery partition.
4. From what I have read, 20gigs is too small for a Vista partition. Research this.
5. Make the separate Media partition a FAT or NTFS partition. Ubuntu read/writes to them just fine.
6. Suspend/hibernate takes a lot of ram. Adjust your /swap accordingly.
7. You might need EasyBCD to help with any bootloader problems that crop up...
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by dougleduck on 2009-02-07
I doubt I'll be using vista at all ( don't use it anymore), but be keeping it anyway.

I'll go for bit bigger vista partition like you said.

Are there problems with the grub boot loader and vista? I'd rather use that than the vista boot loader. 

Is it right that vista uses multiple partitions?

---

### Post by mkvnmtr on 2009-02-07
About 10 or 15 GB is big enough for any linux distro if you have a big home. For all of them you can use th same swap. Ihave only 40 GBon one laptop but have windows on a little partition and two linux distros. Grub should replace the windows boot partition. I think if I had your hard drive I would have 3 or 4 partitions for different linux distros just to play. Every time you install one grub seems to see all of them.

---

