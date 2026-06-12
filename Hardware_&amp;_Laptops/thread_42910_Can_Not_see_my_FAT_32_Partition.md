---
title: "Can Not see my FAT 32 Partition"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by MountainDude on 2005-06-19
Hello

I just installed Ubuntu Linux
I have about a blank 500mg Fat32 
Partition.This is so I can transfer files
from linux to windows. After looking up how 
to see this partition in linux for quite
some time, I have given up.

So if you could please help me
That would be much apreciated

Thanks

---

### Post by tread on 2005-06-19
We just went through a long session here :)
[http://ubuntuforums.org/showthread.php?t=42845](http://ubuntuforums.org/showthread.php?t=42845) 

Check it out .. it might help.

---

### Post by Arktis on 2005-06-20
Or, you can simply check out ubuntuguide.org ;)
They have sections on mounting windows partitions for read/write, and once you figure out the correct command to type for your fat32 partition, you can put an entry in /etc/fstab that will automaticly mount the partition as read/write for you each time you boot. You can even do this with ntfs, so you don't even need to use your 500 mb "mediatory" partition... though it may be good to use. Last I heard (and this was at least a year or more ago) linux had trouble writing to ntfs (but not fat32) and no trouble reading ntfs.

So you may want to mount your 500 mb fat partition as read/write and then mount your ntfs partition as read ONLY.

---

