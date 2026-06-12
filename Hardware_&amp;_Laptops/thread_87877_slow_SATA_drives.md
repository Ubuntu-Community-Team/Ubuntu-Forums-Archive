---
title: "slow SATA drives"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by waster on 2005-11-09
Hello,

I have two SATA drives in RAID 1 on a clean Breezy install on AMD64.

hdparm -i /dev/sda and /dev/sdb show that the data transfer rate from the disk is very low ~20 megabytes/s. The cache speed is very high.

hdparm appears only to be able to tune IDE disks, so do any forum members have the same problem, or suggestions for solutions?

Thanks,
Jack

---

### Post by frodon on 2005-11-09
In my case hdparm never solved my disk problem (IDE) but adding the amd module in /ets/modules solved completely my issue.
So open your /etc/modules file and add this line in first position : **amd74xx**. It works with the 32bits kernel, i'm not sure it works with the 64bits kernel.

Let me know if it works or if you use the 64bits kernel.

---

### Post by waster on 2005-11-09
Thanks for the reply. That module is already loaded and in use, according to lsmod.

This is in /proc/ide/amd74xx

<code>
----------AMD BusMastering IDE Configuration----------------
Driver Version:                     2.13
South Bridge:                       0000:00:06.0
Revision:                           IDE 0xa2
Highest DMA rate:                   UDMA133
BM-DMA base:                        0xf000
PCI clock:                          33.3MHz
-----------------------Primary IDE-------Secondary IDE------
Prefetch Buffer:              yes                 yes
Post Write Buffer:            yes                 yes
Enabled:                      yes                 yes
Simplex only:                  no                  no
Cable Type:                   40w                 80w
-------------------drive0----drive1----drive2----drive3-----
Transfer Mode:        DMA       DMA       PIO       PIO
Address Setup:       90ns      90ns      30ns      30ns
Cmd Active:         300ns     300ns      90ns      90ns
Cmd Recovery:       300ns     300ns      30ns      30ns
Data Active:        330ns     330ns      90ns      90ns
Data Recovery:      270ns     270ns      30ns      30ns
Cycle Time:         600ns     600ns     120ns     120ns
Transfer Rate:    3.3MB/s   3.3MB/s  16.6MB/s  16.6MB/s

</code>

Any more ideas would be much appreciated.

Thanks,
Jack.

---

