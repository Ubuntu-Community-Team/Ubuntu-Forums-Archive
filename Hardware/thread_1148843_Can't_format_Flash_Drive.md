---
title: "Can't format Flash Drive"
date: 2009-05-04
forum: Hardware
---

### Post by MasterNetra on 2009-05-04
I recently got a 8GB flash drive, but it has the fat32 filesystem and I've tried formating it to NTFS in windows xp and windows couldn't do it (I even optimized it for performance so the NTFS option was available but the format failed) any thoughts? Also would it be possible to format it to a blank ext4? (Though it would become incompatible with a windows OS but meh.) Also the drive is from China but its size isn't doctored as I've reccently finish stuffing over 7GB worth of data into it without issue. I would just like to be able to use the remaining space. (7.79 GB Total available, but US brands with Fat32 I hear are simlair in actual capacity)

---

### Post by taurus on 2009-05-04
See if you can gparted to format it to ext4.  Don't forget to unmount it first before you format it though.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
```
System -> Administration -> Partition Editor

p.s.  Back up your data from the drive first before you attempt to reformat it.

---

### Post by MasterNetra on 2009-05-04
I had hoped to get the full 8GB (or at least around 7.99 or something) but i guess not happening, a little less then 7.79 but at least I can use Gparted to setup a ntfs partition on the drive, and later change it to ext4 when i graduate from college. Thanks (I should of thought about using Gparted before, but meh.) Now if i can only get into my room which i so thoughtfully locked myself out of... >.>

---

### Post by mikedep333 on 2009-05-05
First of all, hard drive and flash memory manufacturers define a a gigabyte differently than operating systems do.
Manufacturers: 1,000,000,000 bytes
Operating Systems: 2 to the 30th power bytes = 1073741824 bytes
Therefore you should have about 7.45GB, unless they're generous and give you more.

So why exactly do you want to format it away from FAT32? The only major reason for doing so is to put files larger than 4GB (a FAT32 limitation.)

For USB flash drives, ext2 is more appropriate I believe. For one thing windows computers with ext2fsd installed can access it.

---

