---
title: "Problems formatting external HDD"
date: 2016-08-28
forum: Hardware
---

### Post by SteveTyrer on 2016-08-28
I am using Ubuntu 16.04 LTS and am trying to recover a HDD from a failed Raid 0 array.
The drive was locked but I unlocked it using hdparm which worked fine. Ubuntu Disk is showing the drive as unknown and when 
[ATTACH=CONFIG]270918[/ATTACH]

I try to format it I get the following

  [ATTACH=CONFIG]270917[/ATTACH]
Any help would be appreciated.

---

### Post by yancek on 2016-08-28
When you say you are trying to recover the HDD, do you have data on it?  Hopefully not because formatting it will remove data.
Did you try the suggestion at the top of your second image, basically creating a partition and then a filesystem on it?

---

### Post by SteveTyrer on 2016-08-28
Data loss is not a problem, when I tried creating a new partition I get a read/write error even after confirming that the drive has not locked itself, starting to think that the drive has failed  and is not recoverable..

---

