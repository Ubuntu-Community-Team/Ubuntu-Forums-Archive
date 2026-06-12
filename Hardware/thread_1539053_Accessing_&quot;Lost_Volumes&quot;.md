---
title: "Accessing &quot;Lost Volumes&quot;"
date: 2010-07-26
forum: Hardware
---

### Post by Highstaker on 2010-07-26
VAIO: Recovering "Lost Volume" data

Hello everyone. There is a problem with my Sony VAIO PCG-GRX670. My windows has crashed and I don't see any way to revive it without formatting.

I have a 40 GB HDD, it is initially split into 18 and 22 GB (C: and D: ).
The problem is that, whenever I try to access the HDD, whether I do it from Windows XP Live CD, Ubuntu Live CD or some utilities (like Norton Commander - like programs and Partition editors), it is either not recognized whatsoever, or recognized as a whole unpartitioned 40 GB drive, and I see only the contents of C:. They say that the amount of occupied space is about 37 GB, which is true if you sum the amount of occupied space on C: and D:. But, they dont recognize it as a split disk, and (the main part) I cannot access the data I have on D: . 
When I access the 40 GB file system on Ubuntu and run "fdisk -l", it gives:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21d565dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+  44  Unknown

The question is, is there any way to access the D: from Ubuntu, so I could backup my data from it onto a USB Hard disk? 

Thanks in advance.

---

