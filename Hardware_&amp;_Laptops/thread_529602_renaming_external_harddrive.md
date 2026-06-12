---
title: "renaming external harddrive"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by johnapeterson on 2007-08-19
Hey,
I reformated an external usb hard drive from ntfs to ext3 (after backing up the data on it).  Now external harddrive is labeled as "disk" on the desk top.  I want to rename it to "music files".  What is an easy way to do that?

Thanks,
John

---

### Post by Total_Biscuit on 2007-08-19
Using e2label to label the first partition on the USB disk ought to work.  Otherwise, you could discover the joys of custom udev rules - take a look at [http://ubuntuforums.org/showthread.php?t=164902](http://ubuntuforums.org/showthread.php?t=164902).

---

