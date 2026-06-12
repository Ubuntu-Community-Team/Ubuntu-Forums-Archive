---
title: "Unable to partition USB hard drive"
date: 2011-03-25
forum: Hardware
---

### Post by barlaso on 2011-03-25
I assembled a USB hard drive from a 250gb laptop disk and a cheap 2.5'' enclosure.  The hard disk comes from a windows laptop, has 3 ntfs partitions on it.  I tried to repartition the drive using gparted and testdisk.  Each time, it seems to work (no errors), but the partitions remain intact.  I guess the new partition table is not written on disk.  Is there a hardware switch or similar that I need to flip?

---

### Post by .:PiXi²:. on 2011-03-25
Which controller are you using in the enclosure? Or do you have details on the enclosure?

---

### Post by barlaso on 2011-03-25
This is the one:
[http://www.amazon.com/gp/product/B001AAVA08](http://www.amazon.com/gp/product/B001AAVA08)

---

### Post by .:PiXi²:. on 2011-03-25
The enclosure has no interface and just a minimal controller, so that can't be causing troubles. I suggest to format the whole disk using disk utility (palimpsest) first before adding new volumes. Or have you tried this already?

---

### Post by barlaso on 2011-03-25
Yes I tried this also, same result.  Disk utility shows it has formatted the entire drive, but when I remount, the partitions are back.

---

### Post by oldfred on 2011-03-25
Testdisk is more for recovering deleted partitions. You should just need gparted.

With gparted did you click on the check in top panel to finalize the changes. All the changes are not done as you build the table but only after you confirm you want to make the changes.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by barlaso on 2011-03-25
Yes, I tried several programs.  I committed the changes in gparted.  testdisk also has tools which rewrite partition tables, none of these changes seem to stick.

---

### Post by barlaso on 2011-03-25
In fact I think I lack any write capability at all.  I tried to copy some files, they seemed to copy fine, but disappear after unplug/replug.  I'm doing everything with sudo, and have all ntfs utils installed.  I have write support enabled in the ntfs config tool.

---

