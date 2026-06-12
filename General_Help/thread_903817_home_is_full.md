---
title: "/home is full"
date: 2008-08-28
forum: General Help
---

### Post by sstecken on 2008-08-28
According to the Disk Usage Analyzer, my /home directory is 100% full.  I am unable to save any new files to my computer.  I still have nearly 100GB of free space on the disk.  What gives?

---

### Post by snowpine on 2008-08-28
How is your hard drive partitioned? Did you put /home on its own partition? If so, you can use the GParted Partition Editor (from the Live CD) to enlarge your /home partition, possibly shrinking one of your other partitions to make room.

---

### Post by sstecken on 2008-08-28
That's what I thought at first; then I opened up GParted to find I only have 2 partitions - the main ext3 partition and the swap.  That's what I don't understand.

Is there some default limit on how much space a particular user is allowed to take on the drive?  It seems pretty arbitrary to be allocated only 31.2GB for a user when I have another 107GB free.

---

### Post by mocoloco on 2008-08-28
I think this is just a misunderstanding :)  The disk usage analyzer shows what percentage of the scanned area is being used by what folders.  When you scan your home folder it will always show it as using %100.  If you were to scan your whole file system you would see a different percentage for your home folder.  Make sense?

---

### Post by sstecken on 2008-08-28
Sure, that makes sense.  If I do a full scan, it shows up as 90.4%, not 100%.  I suppose now that it's saying, "Of the 100% of data that is actually on the disk, 90.4% of it is in /home."  Anyways, the deb package I was attempting to save said, "There is not enough room on the disk to save /tmp/randomjumbo.deb.part."

Alright, so now I understand that my drive is not in fact full and that it is a problem with the /tmp directory, not /home as I had thought before.  Is this due to permissions?

---

### Post by drs305 on 2008-08-28
mocoloco is correct. the top directory always shows 100% in disk usage analyzer. 

some people also get erroneous reading because the .gvfs (g virtual file system) apparently doubles the reported size of your drive. if this happens there should be an option in Preferences to untick the .gvfs folder in your home partition.

To check your partition usage via CLI, run:
```
df -Th | grep dev
```

---

