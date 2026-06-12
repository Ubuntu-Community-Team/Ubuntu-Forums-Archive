---
title: "Filesystem is missing"
date: 2008-07-27
forum: Hardware
---

### Post by telemarker on 2008-07-27
Hi,
I've a Maxtrox 6Y160P0 external HD, that I used several times with both Windows and Ubuntu. 
Some time ago it stopped working: it is no more recognised by Ubuntu, and if I use GParted to analyse it, it returns me a Warning:

[INDENT]
Unable to detect filesystem! Possible reasons are:
-The filesystem is damaged
-The filesystem is unknown to GParted
-There is no filesystem available (unformatted)
[/INDENT]

Does anyone knows haow can I give this device a new filesystem without loosing all the files that it contains?

Thanks a lot

---

### Post by argosreality on 2008-07-27
I'm assuming you ment Maxtor as the maker of the drive? If so, download their dos based CD to test the drive to see whether its failed or not. If its failed, your data is most likely lost unless you want to send it to an expensive data recovery center (Seagate charges $1k plus starting whereas ontrak or similar services can go from $600 to much, much more and there's no promise you'll get any data)

What file system was originally on it? NTFS or ext3 or...?

---

### Post by telemarker on 2008-07-28
The filesystem was FAT32, for data storage.
The check with the dos cd is failed... 
Think I will format the disk and then trying to ricover the data, if they are not all deleted.

---

### Post by argosreality on 2008-07-28
> **telemarker said:**
> The filesystem was FAT32, for data storage.
The check with the dos cd is failed... 
Think I will format the disk and then trying to ricover the data, if they are not all deleted.If the drive failed its check then most likely its toast, you probably won't be able to recover much data...if at all

---

