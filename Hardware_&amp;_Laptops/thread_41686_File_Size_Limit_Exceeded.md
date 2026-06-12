---
title: "File Size Limit Exceeded"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by matthew on 2005-06-14
I recently backed up my system using the method posted in [this howto](http://www.ubuntuforums.org/showthread.php?t=35087).  The backup seemed to work fine. However, I would like to copy the file to a portable hard drive that is formatted with FAT32 because it also gets used occasionally with Windows systems (at least until I get a few more things running under linux).

Here's my problem, I try to copy the 5.1 Gb file from my ext3 hdd and put it on the FAT32 drive only to wait a long time and receive a File Size Limit Exceeded message when running in a terminal window.

So, does FAT32 really have such a low file size limit? Is this something that I can modify? If not, is there another filesystem that I can change to on that drive without destroying my data and which will be readable in Windows?

---

### Post by Alexander Kirillov on 2005-06-14
[QUOTE=matthew]I recently backed up my system using the method posted in [this howto](http://www.ubuntuforums.org/showthread.php?t=35087).  The backup seemed to work fine. However, I would like to copy the file to a portable hard drive that is formatted with FAT32 because it also gets used occasionally with Windows systems (at least until I get a few more things running under linux).

Here's my problem, I try to copy the 5.1 Gb file from my ext3 hdd and put it on the FAT32 drive only to wait a long time and receive a File Size Limit Exceeded message when running in a terminal window.

So, does FAT32 really have such a low file size limit? Is this something that I can modify? If not, is there another filesystem that I can change to on that drive without destroying my data and which will be readable in Windows?[/QUOTE]
 FAT32 indeed has file size limit of 4 Gb:
[http://www.ubuntulinux.org/wiki/LinuxFilesystemsExplained](http://www.ubuntulinux.org/wiki/LinuxFilesystemsExplained)

---

### Post by jkndrkn on 2005-06-14
Try modifying the HowTo by creating a couple smaller tar files instead of one larger one.

---

### Post by matthew on 2005-06-14
Both replies were helpful. Thank you!

---

