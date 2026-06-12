---
title: "Help removing partition"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by hdjunkie on 2009-02-24
I looking to install ideneb on top of windows 7, and ubuntu.  Between the two installations, there are now 4 partitions on my hard drive (the maximum).
One of the partitions is the swap drive, and another is a "SYSTEM" drive that windows apparently partitioned during install.  The other two are obviously the main boot drives for windows, and ubuntu.  I created a drive letter for the system drive, but it appears empty (hidden files are shown, protected os files are shown).
I've also read that the swap drive isn't necessary as it's used for dumping the ram for hibernation etc.  I should say that I read that you can create a swap file that performs the same function with the same results.
Anyways, I guess my question is which partition should/can I remove to make another partition for OSX?  I'll be using the grub bootloader to access windows, ubuntu, and osx.

---

### Post by cariboo on 2009-02-24
The swap partition is used when you run out of ram, to help the system keep running, instead of crashing like windows does.

Jim

---

### Post by hdjunkie on 2009-02-25
Yes, that's what I was trying to say.  But it's my understanding that you don't need to have a swap "partition" but you can simply create a swap "file" on the same partition.

---

