---
title: "Promise Fastrak66 IDE RAID 1 array shows both drives"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by robertw on 2007-09-24
I have installed Ubuntu 7.? desktop onto a very basic setup, one IDE hard drive for system, graphic card and nic.  Next I added a Promise Fastrak66 ide raid with ntfs hd drives configured RAID 1 from a windows 2000 box.  During boot, the Promise bios shows the array as functional.  However, the computer browser shows 2 files: New File and New File(2).  I thought the raid card would make the array appear as one hd, but I see both and apparently can write to either but not both at the same time as a properly functioning array would do.  Qtparted also shows both hard drives.  What is even more confusing is that this is the second time I have installed the system, and the first time I thought I did the same thing and only saw one drive.  Any suggestions?

---

### Post by overdrank on 2007-09-25
> **robertw said:**
> I have installed Ubuntu 7.? desktop onto a very basic setup, one IDE hard drive for system, graphic card and nic.  Next I added a Promise Fastrak66 ide raid with ntfs hd drives configured RAID 1 from a windows 2000 box.  During boot, the Promise bios shows the array as functional.  However, the computer browser shows 2 files: New File and New File(2).  I thought the raid card would make the array appear as one hd, but I see both and apparently can write to either but not both at the same time as a properly functioning array would do.  Qtparted also shows both hard drives.  What is even more confusing is that this is the second time I have installed the system, and the first time I thought I did the same thing and only saw one drive.  Any suggestions?

Hi maybe this link will help
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by robertw on 2007-09-27
Thanks.  I had come across this info and have replaced the card with a true hardware raid card (3Ware 9500s-4lp) which also supports many flavors of Linux.  It works fine.

---

