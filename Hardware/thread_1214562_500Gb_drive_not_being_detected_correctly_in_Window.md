---
title: "500Gb drive not being detected correctly in Windows"
date: 2009-07-16
forum: Hardware
---

### Post by jadhav333 on 2009-07-16
I have a dual boot machine.. One of my harddisk is 500Gb seagate IDE. I intend to use this as my Data drive..

The drive is properly detected as 500Gb in Linux/Ubuntu. 

When I boot in windows, the drive is incorrectly detected as 130Gb. Also any attempt to access this drive results in a message asking me to format the drive.

What is the issue between my harddrive and Windows :?

---

### Post by lisati on 2009-07-16
What format is it? Windows doesn't natively support ext3.....

---

### Post by Chaos Punk on 2009-07-16
Ubuntu and Windows are probably seeing different partitions than eachother, can you check how many partitions are on the drive?

---

### Post by jadhav333 on 2009-07-19
I have tested with fat32 and ntfs as well.. and I am refering to the same drive in both windows and linux.. 

even if I do a cold setup from windows using only the drive in question.. the setuo shows the drive as 130 Gb.. 

If I do the same with linux, it is shown as 500GB..

---

### Post by Whiffle on 2009-07-19
You need to install Service Pack 3 for Windows.  Old versions of XP have a 130 gb limit.

---

