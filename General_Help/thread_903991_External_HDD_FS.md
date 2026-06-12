---
title: "External HDD FS"
date: 2008-08-28
forum: General Help
---

### Post by PurposeOfReason on 2008-08-28
I have a 1TB external HDD that I want to be able to read and write in windows and linux. I can't use FAT32 because of the 4GB limit. I will also be sharing this drive through my uni's network if that matters.

---

### Post by Lord Xeb on 2008-08-28
Use NTFS or something It works with Ubuntu But I am not sure about Arch.

---

### Post by unutbu on 2008-08-28
How about make the drive ext3 and use ext2IFS 
[http://www.fs-driver.org/](http://www.fs-driver.org/) to let Windows read/write to  the ext3 filesystem?

---

### Post by PurposeOfReason on 2008-08-28
NTFS is my best bet at the moment. It works in both but it does fragment easier. I would use ext3 but I'm not sure if other people could read it.

---

