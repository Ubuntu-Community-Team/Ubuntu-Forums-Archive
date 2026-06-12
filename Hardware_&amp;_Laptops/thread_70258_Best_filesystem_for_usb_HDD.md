---
title: "Best filesystem for usb HDD?"
date: 2005-09-29
forum: Hardware &amp; Laptops
---

### Post by RadixLecti on 2005-09-29
I have two questions,

1) What is the best file-system to use on a 40 Gb USB-HDD, if I want to share files with windows? Some files are quite big, up to four Gb.

2) How the heck do I remove the read-only tag on my USB drive? It's currently using ntfs, and works well with my windows laptop. I've tried chowning it, both as user and as root, no good.

Hopefully someone will have an answer for me. ;-)

Addendum: I have all the linux-ntfs files installed. I have tried removing and reinstalling them, no use.

---

### Post by Gezzer on 2005-09-29
FAT32  is the bridge file system between linux & windows
as they both can read/write to/from it ...

---

### Post by RadixLecti on 2005-09-29
Thanks, I'll give it a whirl.
Whatever happened to Captive ntfs?

---

### Post by dannotdan on 2005-09-29
FAT32 limits file size to 4gb. If you ever exceed 4gb I am not sure what you would use. I've played around with several solutions (Captive NTFS, ext for Windows, etc.) and I haven't been satisfied with any of them.

---

### Post by niw_uk1964 on 2005-09-29
[QUOTE=dannotdan]FAT32 limits file size to 4gb. If you ever exceed 4gb I am not sure what you would use. I've played around with several solutions (Captive NTFS, ext for Windows, etc.) and I haven't been satisfied with any of them.[/QUOTE]

I have a 30GB portable usb drive formatted with FAT32. Both ny Linux and WinXp system have no problems seeing and writing to it.

---

### Post by dannotdan on 2005-09-30
niw_uk1964  , please read my post again. I did not say FAT32 limits the partition to 4gb, I said it limits individual files to 4gb.

---

### Post by Velox Letum on 2005-10-01
Also, writing to NTFS is VERY VERY unstable. FAT32 is the best way to go if you're bridging between OSes. If you need to write files bigger than 4gb, you might consider no-compression multiple archive raring, basicly just splitting the file into pieces.

---

