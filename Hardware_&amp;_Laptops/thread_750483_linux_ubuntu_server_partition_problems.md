---
title: "linux ubuntu server partition problems"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by Drate on 2008-04-09
From what I just read about [Dynamic Disk ]("http://www.computerperformance.co.uk/Litmus/disk_dynamic.htm") it looks like a generally bad idea.  It appears to be similar in use to LVM with Linux but with less features.  My recommendation (take it with TWO grains of salt please) would be to backup your data from the dynamic disk hard drive and reformat as something both sides can read commonly (such as fat32 or even ntfs with the ntfs-3g driver).  You can always use linux utils to resize your partitions as needed later if it becomes problematic with "static" partitions.  It CAN be a dangerous operation but it CAN be an easy one as well so just be sure to backup often and adjust as necessary.

This is my recommendation.  Anyone know better do not be shy about over-ruling me.

---

