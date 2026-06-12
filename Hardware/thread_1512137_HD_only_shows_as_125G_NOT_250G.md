---
title: "HD only shows as 125G NOT 250G"
date: 2010-06-17
forum: Hardware
---

### Post by Alligator on 2010-06-17
Here's a strange one.  HP video chips n/s on a laptop, so I took out HD to use as an external drive and get data off. Laptop was running Ubuntu 9.?  Plugged the external drive into a Ubuntu 10.04 machine and the 250G HD loaded as a 125G with a file structure named Public and type of msdos.

fdisk -l

Disk /dev/sdc: 125.0 GB, 125029669888 bytes
255 heads, 63 sectors/track, 15200 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00095ef4

the drive is a samsug HM250J1  250G  So any clues?   I formatted to FS ext3, but only 125G.

---

