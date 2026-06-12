---
title: "Selecting a file system for a external HD."
date: 2008-08-08
forum: Hardware
---

### Post by leetleo on 2008-08-08
Hi! I will soon be installing Ubuntu (dual boot with Vista) on my dell inspiron 1720 for the first time. I recently purchased an external HD (750gb) to store movies/music/personal files etc, but I was wondering which file system to use on this drive. I'm not too keen on exactly how well Ubuntu interacts with NTFS, but I'd prefer it to FAT32 because of filesize limitations and supposed performance issues with large volumes on FAT32. Will I run into any problems using NTFS on my external HD with Ubuntu, or am I free to abandon FAT32. If there are any additional considerations I may be overlooking, please let me know. Thanks :)

---

### Post by silkstone on 2008-08-08
You should be OK with NTFS - Hardy will read/write to NTFS and you can format with gparted.

I think it's better not to format with Vista, although XP is OK.

You could use Ext3 but Windows will not recognise that unless you install an additional driver.

---

### Post by logos34 on 2008-08-08
shouldn't have a problem.  Hardy comes by default with the NTFS-3G driver, which allows you write access to NTFS.

---

### Post by leetleo on 2008-08-08
Thanks for the info guys, I look forward to my first cup of Ubuntu :D

---

### Post by QED CONTrOL on 2008-08-08
Sure, it's easy to say, "use NTFS", but is it the best filesystem to use on your external... for your purpose?

I think there's more to know before you decide.

I found a page that compares the filesystems available to Ubuntu.  There _really is_ a difference.

[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

Check it out 'n let us know your choice.

---

