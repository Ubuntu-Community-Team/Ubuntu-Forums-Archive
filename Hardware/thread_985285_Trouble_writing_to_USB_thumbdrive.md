---
title: "Trouble writing to USB thumbdrive"
date: 2008-11-17
forum: Hardware
---

### Post by iamshawnrice on 2008-11-17
Hi.

I am running Ubuntu 8.04 and am trying to add a 5.5GB file to my 16GB Kingston thumb drive.

There is an error, claiming the file is too large.

The file system is FAT32, which I understand has a 4GB size cap.

How do I change this?

---

### Post by cariboo on 2008-11-17
To get past the fat32 4Gb limit, you will have to reformat the device to a file system that will support file sizes larger than 4Gb. If you use the device in Windows and Linux, I would suggest formatting it as NTFS.

Jim

---

### Post by iamshawnrice on 2008-11-17
Nice...thank you.

---

