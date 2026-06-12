---
title: "Which file system to use?"
date: 2008-05-30
forum: Hardware
---

### Post by Dan++ on 2008-05-30
I'm about to format a 500GB disk for storing my music, documents, etc, which will be accessed by both my Ubuntu Hardy partition (80GB hard disk) and my Windows XP Pro partition (also 80GB hard disk).

I'm not sure which file system to format it as. FAT32 was the obvious one to think of but I've heard it doesn't support file sizes larger than 4GB, which will be a problem.

Can anybody recommend what I should do?

Thanks.

---

### Post by logos34 on 2008-05-30
Either way, NTFS or ext3...When I still had XP on my machine (just sitting there taking up disk space like the bum it was) I had music and docs on a D: drive and used ntfs-3g in linux (now included by defualt in ubuntu) to read/write to it. Worked ok, no issues, but slower copy/write times.

Yes, avoid fat32 (4gb file size limit, less secure, even worse fragmentation).  

Personally I'd go with ext3 and use **fs-driver** to access it on the windows side.

---

