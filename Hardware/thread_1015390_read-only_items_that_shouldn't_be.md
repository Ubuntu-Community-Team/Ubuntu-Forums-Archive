---
title: "read-only items that shouldn't be"
date: 2008-12-18
forum: Hardware
---

### Post by lilas1024 on 2008-12-18
I received my Dell Mini 9 yesterday with Ubuntu. I want to be able to work on documents on both the mini and my regular laptop, transferring them via my flash drive. Ubuntu says my flash drive is read only even though I can save and delete files from it on my Windows laptop. I am using a Memorex brand flash drive.

I have a similar issue with Word Perfect docs showing as read only in Open Office.

---

### Post by camionrouge on 2008-12-19
Hi, this sounds like the file permission has changed to read only.
Select the file that's read only with a single click and then go to File > Properties > Permissions and check if it's read only. If so change it to Read and Write. Close window. You should be able to select a block of files and change permissions for them all in this way.

---

### Post by lilas1024 on 2008-12-19
Thank you. Actually the issue ended up being my own fault. I turned on the lock on my flashdrive. Duh. Problem solved.

---

