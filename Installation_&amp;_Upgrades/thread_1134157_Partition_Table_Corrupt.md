---
title: "Partition Table Corrupt"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Tsarevich on 2009-04-23
My partition table is unreadable by parted (that's why I can install only Mandriva from within the distros I have). I cannot partition my hard drive (using the old partitions). I have to preserve data as well as partition the disk. Is there any way to correct the table?

---

### Post by drs305 on 2009-04-23
There is an app called testdisk which does a good job of repairing partition tables. Doing a search of "testdisk" and "deep search" will probably get you some good links on these forums. 

The post in the middle of this thread gives pretty good instructions:
[http://ubuntuforums.org/archive/index.php/t-1084280.html]("http://ubuntuforums.org/archive/index.php/t-1084280.html")

The entry is archived so I can't give the post number, but it's from caljohnsmith and starts with "Your partition table..."  March 2, 06:12 AM

---

### Post by Tsarevich on 2009-04-23
OK I also ran testdisk, and a "Deep Search". Now how do I mark the partitions? All partitions except the SWAPs are giving file listings. The Linux Partition is the one which I use for Ubuntu (my GRUB is also lost at the moment). The FAT32s are common in Ubuntu and Windows.

---

### Post by drs305 on 2009-04-24
The partition table you posted looks correct. If you really did have one primary and the rest logical I would go ahead and write that to disk and attempt to remount it. When you hit Enter from the page you are on in testdisk it will advance and give you the option to quit or write to disk. 'Quit' actually takes you back to an earlier menu.

---

### Post by Tsarevich on 2009-04-24
I actually got it written and installed Intrepid, thanks. Instead of starting a new thread for this question, can you tell me how do I make an ISO from the files already on HD?

---

