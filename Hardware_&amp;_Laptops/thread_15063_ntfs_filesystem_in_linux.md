---
title: "ntfs filesystem in linux"
date: 2005-02-11
forum: Hardware &amp; Laptops
---

### Post by ianshriver on 2005-02-11
I have two external hard drives that i am trying to mount onto linux, but i am having a lot of trouble.  I was wondering if anyone knows either how to do this or how to reformat to a file system that will work with linux.  I hear fat32 is plug and play with linux but whenever i try to reformat my 250 gig with windows to it it sais that the hard drive is too big, is  there a way to reformat from ntfs to fat 32 on linuix or a way to get ntfs to work with linux.

---

### Post by Hendrin on 2005-02-11
The maximum a FAT32 drive can be is 4GB.

---

### Post by Hendrin on 2005-02-11
Right from Microsoft's site:

In theory, FAT32 volumes can be about 8 terabytes; however, the maximum FAT32 volume size that Windows XP Professional can format is 32 GB. Therefore, you must use NTFS to format volumes larger than 32 GB. However, Windows XP Professional can read and write to larger FAT32 volumes formatted by other operating systems.

I do know currently that Linux can read NTFS filesystem but can't write to them (that may have changed, I just got back into Linux after a two year absence).

---

