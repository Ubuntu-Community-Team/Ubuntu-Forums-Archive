---
title: "Best FS for data storage?"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by ignavia on 2005-04-22
I wouldn't dare ask the general "best FS" question... But if the OS isn't running off the partition, and no swap and all that, is any one FS better than another for data storage on a secondary drive? My secondary drive is currently FAT32, because I was dual-booting with XP, but I quit that now and am an Ubuntu-only fella, so there's no reason to keep the vfat around.

---

### Post by jdodson on 2005-04-22
[QUOTE=ignavia]I wouldn't dare ask the general "best FS" question... But if the OS isn't running off the partition, and no swap and all that, is any one FS better than another for data storage on a secondary drive? My secondary drive is currently FAT32, because I was dual-booting with XP, but I quit that now and am an Ubuntu-only fella, so there's no reason to keep the vfat around.[/QUOTE]

ext3 would be fine for file storage.  i dont think you would notice the speed increase of reiser and ext3 is more "rock solid*." which is what i would go for in a file storage area.

* - please don't flame me. :)

---

### Post by mrtaber on 2005-04-22
I too refuse to enter into a flame war.  I do a lot of work with sound files that can get very large...I use the XFS file system--it was created for large media files (think Silicon Graphics).  It's been rock solid for me, and I did notice the speedup.  However, it's not for everybody (deletes are slow), but if you work with large  files, carve out a partition for it and give it a try.

On the other hand, for my OS partition, I used the dependable (yes, rock solid!) ext3.

Cheers,
Mark Taber :-D

---

### Post by ignavia on 2005-04-22
[QUOTE=mrtaber]I too refuse to enter into a flame war.  I do a lot of work with sound files that can get very large...I use the XFS file system--it was created for large media files (think Silicon Graphics).  It's been rock solid for me, and I did notice the speedup.  However, it's not for everybody (deletes are slow), but if you work with large  files, carve out a partition for it and give it a try.

On the other hand, for my OS partition, I used the dependable (yes, rock solid!) ext3.

Cheers,
Mark Taber :-D[/QUOTE]
 I have some TV shows that approach 1GB and some that exceed that, but I never edit them, only read from them to watch. Is XFS mainly for rewrites to large files? Would I be better off with ext3?

---

### Post by mrtaber on 2005-04-22
XFS is very good (and fast, i.e. optimimzed for) reading and writing large multimedia files.  I've found that to be true, for my uses.  That's why I said to set aside a partition for it, and give it a try before committing :)

Mark

---

