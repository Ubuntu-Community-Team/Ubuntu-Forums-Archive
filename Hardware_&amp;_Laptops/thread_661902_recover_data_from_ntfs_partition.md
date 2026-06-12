---
title: "recover data from ntfs partition"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by p1977p on 2008-01-08
my friend has a laptop with a single 40 GB windows Xp partition formatted as ntfs. the windows installation got screwed up due to some virus and it wont start (in any mode -- dos/safe, etc). He has important data in his my documents folder (upto 6 GB). i have a ubuntu live CD but the problem is that i can't backup to another folder on the hard drive since it is mounted as a readonly filesystem. can someone tell me how to change that and make the disc writable?

---

### Post by keithacole on 2008-01-08
ive battled this for about a year now..

my only suggestion is to run chkdsk on the disc via windows, i havent found any linux utility that can run chkdsk on ntfs partitions properly

i have a bad 300gb ntfs harddrive in my ubuntu box, only reason i havent pulled the data is because i dont want to install windows just to do it, when i get the time ill put another hard drive in there and install windows on it, and then ill chkdsk that bad ntfs drive and get my media back

---

### Post by p1977p on 2008-01-08
thanks, but the thing is that the XP came preinstalled, and i don't have the administrator password that is required during repair

---

### Post by jeffus_il on 2008-01-08
Got a diskonkey ( usb stick) to copy important data to,
could be easy.
There are ntfs updates with write support. See:
[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

Also consider an external USB drive.

---

