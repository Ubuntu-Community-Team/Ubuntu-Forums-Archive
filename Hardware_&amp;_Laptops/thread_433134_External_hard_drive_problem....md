---
title: "External hard drive problem..."
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by 2k1stang on 2007-05-04
I've got Ubuntu on my computer right now. However, I want to install Vista again. I installed it once, but forgot to disconnect my external hard drive. Now the only way I can get the data in Windows is with data recovery software. The problem with that is that it isn't organized, etc. etc. How can I remedy the situation?

---

### Post by jack1254 on 2007-05-04
Can you clarify a few things? You had Ubuntu on, and want to switch to Vista, but on the first attempt to do that you had your external HDD plugged in? 

What data are you trying to get at with the data recovery software? Is it on the external HDD or on your internal drive? If your external drive is formated in a "linux" filesystem (ext2,ext3,ReiserFS, etc) then Windows won't be able to read it without some sort of specially designed program (much like data recovery software)

---

### Post by 2k1stang on 2007-05-04
> **jack1254 said:**
> Can you clarify a few things? You had Ubuntu on, and want to switch to Vista, but on the first attempt to do that you had your external HDD plugged in? 


Correct. 

> **jack1254 said:**
> What data are you trying to get at with the data recovery software? Is it on the external HDD or on your internal drive? If your external drive is formated in a "linux" filesystem (ext2,ext3,ReiserFS, etc) then Windows won't be able to read it without some sort of specially designed program (much like data recovery software)

It's on my external HDD. It's formatted in in a fat32 file system. It's music, videos, photos, and a few word documents.

---

### Post by jack1254 on 2007-05-06
It sounds like there might be a problem with the partition table of the drive. This would explain why file recovery software is able to find the files. You want to find a software to "restore" or "repair" the partition table (the "File Allocation Table" in fat32, hence FAT), or because you already have the file recovery software, you might just "recover" the files to another location and then reformat the partition/drive that isn't accessible.

---

