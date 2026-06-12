---
title: "HUGE Fat32 Partition"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by carlossousa on 2007-05-28
Hi there,

Has anyone ever wondered how those super huge external disks, 320GB, 500GB, 1TB, have a single partition on them, that is type FAT32 ?
I have a spare 250Gb disk and enclosure but I can't format it with one partition, to the length of it, in FAT32.
I prefer FAT32 for compatibility reasons between linux and windows.

Can anyone help?

Thanks

---

### Post by Jussi Kukkonen on 2007-05-28
You are doing this in Windows, I assume? For some bizarre reason Windows systems can only create FAT partitions smaller than 32GB, although the filesystem can cope with sizes up to 8TB... 

I suggest you use linux to partition the disk. Don't be surprised if the performance is lousy, though (FAT may be able to handle 8TB, but it sure wasn't designed with that in mind).

---

### Post by Lieter on 2007-05-28
you can also use NTFS, the NTFS-3G drivers for linux are so good that they will not corrupt your data. you can consider that

---

### Post by ep2011 on 2007-05-28
The best way in my opinion would be to use the ubuntu LiveCD to partition the drive in Gparted, which you will be able to make a FAT partion up to 8tb and will make reading and writing easy in both Linux and Windows.

---

### Post by carlossousa on 2007-05-28
Thank you all for your replies!!!

Leiter: I didn't consider using ntfs-ng cause i've encountered some problems relating to big files, as in larger that 1GB. Of course with ntfs it would be nice to have no limit to the file size being stored, but hey, nothing like giving it a try.

---

