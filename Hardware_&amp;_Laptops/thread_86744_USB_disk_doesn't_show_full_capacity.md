---
title: "USB disk doesn't show full capacity"
date: 2005-11-06
forum: Hardware &amp; Laptops
---

### Post by aerials on 2005-11-06
I have a 160 GB USB disk split into two fat32 partitions of ca. 70 GB.
With the first partition everything works just fine, but the second partition won't show me the full capacity of free space. Of that 70 GB, something around 32 GB is used and the rest should therefore be available. But Nautilus and Disks Manager show me only 3.2 GB of free space. I don't see any hidden files on that disk, the trash is empty and under Windows I can get access to the full free space.
Does anybody have an idea what could possibly be the problem?

---

### Post by Teroedni on 2005-11-06
hmm
Maybe windows is using the disk and are preventing ubuntu from accesing.
Are windows installed on the other partition,the one ubuntu cant see?

---

### Post by Confused Fishcake on 2005-11-06
fat32 has a 32Gb disk limit, don't quite know how it works though.

---

### Post by aerials on 2005-11-06
I haven't installed Windows on that machine, I just tested the disk with my sister's computer to find out if it is a Linux issue.

I know about that 32 GB issue, but the first partition works perfect and until today I never had problems with such big fat32 partitions.

---

### Post by Teroedni on 2005-11-06
Go into gparted
It should see it all. If you not got it installed search for gparted in synaptic


edit it was gparted sorry

---

### Post by aerials on 2005-11-06
Thanks for your help. I didn't know gparted yet, only qtparted.

gparted showed me the the correct free space when the usb drive was unmounted, but the wrong amount of free space when the drive was mounted. Since I had made a copy of the data I simply deleted and recreated the partition and now it seems to work.

And about that 32 GB fat32 issue once more: With fat32 you can create partitions up to 2 TB, the 32 GB "obstacle" was introduced by Microsoft with Windows 2000: Partitions > 32 GB could only been formatted NTFS, unless you used 3rd party software. That was Microsofts way to force people to use NTFS.

---

