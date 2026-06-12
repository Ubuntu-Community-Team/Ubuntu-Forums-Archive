---
title: "[SOLVED] Where has my disk space gone?"
date: 2008-10-09
forum: General Help
---

### Post by cknight on 2008-10-09
Using df -h, I can see that the size of my home filesystem is 20Gb, 17Gb of which is used and 1.6Gb is available.  Now, 17 + 1.6 = 18.6.  So where's the missing 1.4Gb?  I realize that file systems aren't 100% effecient and the partition takes up some space but roughly 7.5% of my disk space seems excessive.

---

### Post by fsmithred on 2008-10-10
It didn't go anywhere. Hard drive manufacturers like to think that a megabyte is 10 to the third power, but your operating system uses 2 to the 10th (1024).

---

### Post by drs305 on 2008-10-10
In addition to what fsmithred stated, the system reserves 5% of the disk space for system use (journalling, etc). 

You can alter the percentage with the "tune2fs -m" command but I'm not recommending it. You can read about it in "man tune2fs".

---

### Post by cknight on 2008-10-10
Wow, 5%. That would account for most of it.  Thanks.

---

