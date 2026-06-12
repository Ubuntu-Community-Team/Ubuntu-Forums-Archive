---
title: "Inconsistent md5sum checksums for larger files"
date: 2008-08-16
forum: General Help
---

### Post by hal_bregg on 2008-08-16
Hi!

I recently installed Hardy 64bit edition on my desktop, hoping it'll be my default operating system. 
While trying to burn some cd images I noticed strange md5sum behavior. It generates different checksum each time i use it on the same file. This only happens when generating checksums of files larger than 150 megabytes, no matter where the file is located (flash drive, usb hard disk, sata hard disk).Checksums generated with cksum differ only in the first half, also for files larger than 150 mb.
Memory tests have shown no errors and md5sum under windows vista, on the same machine, has never shown such errors. 
My hardware: Intel Core2Duo E8200 2,66 GHz with 2GB RAM - Kingston DDR2, 800MHz, mainboard: Gigabyte ep35c-ds3r. 
System Ubuntu 8.04 (hardy), kernel 2.6.24-21-generic
What could be the cause of such md5sum behavior?

Mike

---

### Post by jnewm on 2008-10-21
I have the exact same problem.  Anyone have any ideas?

---

