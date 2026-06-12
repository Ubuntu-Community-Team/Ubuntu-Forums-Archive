---
title: "Any way to fix broken raid0 set?"
date: 2013-01-01
forum: Hardware
---

### Post by airworks on 2013-01-01
A while ago when I was still on Windows I had two secondary 1 TB hard drives that used a raid0 setup, fakeraid I believe with Intel. My primary hard drive died which seemed to have messed up the raid as well.

Using dmraid I get the error: "isw: wrong number of devices in RAID set" when trying to use most commands. When trying to rebuild, "Rebuild: raid0 cannot be rebuild". Info when using dmraid -s:

```
ERROR: isw: wrong number of devices in RAID set "isw_bcibgbaaec_Comp" [1/2] on /dev/sdc
*** Group superset isw_bcibgbaaec
--> Subset
name   : isw_bcibgbaaec_Comp
size   : 1953519872
stride : 256
type   : stripe
status : broken
subsets: 0
devs   : 1
spares : 0
```The info for fdisk -l on these two drives:
```
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373
``````
Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
```I can see that the disk identifier of the 2nd drive is showing 0x00000000, which I assume it an issue. No files also under /dev/mapper aside from control.

Other things to mention when using disk utility, the first drive shows "Unknown Scheme" under partioning while the second drive shows "Not Partitioned". The unknown scheme drive still shows many data blocks with labels "Free 112 GB", "871 GB RAID Component", "372 GB RAID", "Free 257 GB", "Free 18446743 TB". Have no idea why it shows so many free space labels as well as 18446743 terabytes? Wow. The not partitioned drive just says "1.0 TB RAID Component".

Does anyone happen to know what could be wrong? Am I able to fix the broken raid? When I boot up the PC it actually says "normal" for the raid status so I was hoping it could be fixed.

If you have any suggestions for what I should try or if you need any additional information, please let me know.

Thanks.

---

### Post by airworks on 2013-01-03
Does anyone happen to know if it will make any difference on a windows operating system? These were just secondary drives though so I figure it shouldn't matter.

---

### Post by airworks on 2013-01-04
Anyone have any ideas? I'm thinking of just breaking the raid... Also feel free to move this thread if this is not the correct section. Thanks.

---

### Post by airworks on 2013-01-07
What would be the best way to break the raid then? Or does it not really matter?

---

### Post by numerialized on 2013-04-19
[http://communities.intel.com/thread/18291](http://communities.intel.com/thread/18291)

---

