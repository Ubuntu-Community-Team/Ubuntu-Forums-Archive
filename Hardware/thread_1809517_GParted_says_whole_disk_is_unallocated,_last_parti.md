---
title: "GParted says whole disk is unallocated, last partition extends past last cylinder"
date: 2011-07-21
forum: Hardware
---

### Post by Mahkoe on 2011-07-21
K, so I'm in ubuntu booted from the hard drive in question. Wanting to satisfy my partition urges, I open up gparted. It says my whole hard drive is unallocated. Okay, I say, it must be because I'm using it or because it's mounted. I whip out my ubuntu live cd, and start gparted, but the program crashes as it scans the devices. I later use the fdisk -l command. It tells me my drive has 38913 cylinders, but that the last partition (which is in an extended partition) ends on cylinder 38914. Anyway, I would like to know what is going on and how I can fix this. Also, I do have a backup of my drive, but I didn't want to use it just yet, because I think there is something wrong with my partitions. Please help

Extra info
Using ubuntu 10.10 32 bit
Hard drive is 320 gb
Hard drive has three primary partitions (associated with windoze), and an extended partition containing swap and ubuntu.

---

### Post by oldfred on 2011-07-21
Several ways, I think the fixparts is probably the easiest. Back up partition table first with whatever you use.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Backup first and save to another drive. sda shown:
sudo sfdisk -d /dev/sda > parts.txt

Manual way:
sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)

---

### Post by Mahkoe on 2011-07-21
Thanks a lot, I'll try that

---

### Post by Mahkoe on 2011-07-21
Sorry to make you wait so long, I had something to do.

I'm sorry to say that fixparts didn't work. I'm not going to get into your second answer now because in my time zone it's almost tomorrow, but i'll be sure to try it, thanks.

---

### Post by srs5694 on 2011-07-21
Please post the output of the following command:

```

sudo fdisk -lu

```

Post the results between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to preserve legibility. This output will show us precisely what your partitions are, which is important information for diagnosing the problem.

It might also be helpful to know what you mean by "fixparts didn't work" -- did it crash, did it fail to see all your partitions, did you write changes but you still have problems, etc.? Also, be aware that FixParts doesn't write most changes to disk unless you use its "w" command, so if you didn't type "w", it won't have done anything useful. (Don't use "w" if the FixParts partition list shows missing or omitted partitions that you want to keep, though!)

---

