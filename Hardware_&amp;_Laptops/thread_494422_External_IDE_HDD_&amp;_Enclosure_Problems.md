---
title: "External IDE HDD &amp; Enclosure Problems"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by rockdude05 on 2007-07-06
Hey guys,

I recently bought a 3.5" IDE USB Enclosure and a 320gb Seagate drive to go with it.

What I am aiming to do is have an external drive that lets me transfer data between windows computers and my ubuntu feisty computer. I know that certain filesystems have restrictions on both OS's, so I came down to either

FAT32 - Works on both, but does this work on large drives?
NTFS - Using ntfs-3g on linux

Originally, it was formatted on a windows pc, as a single NTFS partition, because windows wouldn't let me make it a FAT32 drive under any situation or partition size. NTFS worked fine on the XP machine.

When i plugged the drive into my ubuntu PC, it came up as a drive on the desktop, but read-only. At this point, ntfs-3g and ntfs-config were both installed, so i loaded ntfs-config (latest version) and tried to enable read/write for the external drive which it had recognised as NTFS.

It couldnt do it and came up with an error saying the NTFS filesystem was corrupt, possibly due to an incorrect shutdown etc in windows. So, i went into g-parted, and had a look at the filesystem.

In g-parted, i wasnt able to make a new NTFs partition, so i tried the others.

ext3, ext2, reiserfs - worked, but was mounted only as read only, even after trying various utils to change the mounting options. i assume it encountered errors.

FAT32 - In ubuntu i was able to make an entire FAT32 partition, so i did, and after remounting, the drive came up on the desktop fine, and was read/write capable...

After transferring approx 20gb of data, the drive became unmounted and stopped file transfers. After unplugging the drive and insterting it again, it was unrecognisable as any partition at all, and wouldnt even show up in g-parted.

But, putting it back into the windows machine, it was recognised, and i could, again, reformat it into a working read/write ntfs partition.


Sorry for the essay guys but after trying everything i could, trying on ubuntu livecd and installation... im not sure how to get this working. I hope someone can help me either format the drive with ntfs in ubuntu for read/write... or understand why the FAT32 partition is extremely unstable and tempermental.

Thanks!

---

### Post by tgalati4 on 2007-07-06
Look at dmesg for disk write errors.  You need to see why Ubuntu farted when transferring data in the first place.

It's possible that you didn't break in your drive before using it.  It's a good idea to do a zero-write to the entire drive to make sure you can write to the entire surface.

It's also possible that the drive overheated.  This is common in USB enclosures that don't have fans or are poorly engineered.

FAT32 is an OK file system for static storage of data that will be used by both operating systems.  NTFS and ext3 will give better performance for active use, but then you run into access problems.

---

