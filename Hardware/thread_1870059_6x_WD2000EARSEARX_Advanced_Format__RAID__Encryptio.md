---
title: "6x WD2000EARS/EARX Advanced Format / RAID / Encryption Write Performance Issue"
date: 2011-10-26
forum: Hardware
---

### Post by mriedel on 2011-10-26
I'm using 1x WD2000EARS and 5x WD2000EARX "advanced format" drives in a mdadm RAID 6 on ubuntu 11.10.  With full disk encryption on the RAID array (LUKS),  I get quite low write speeds. Now I know that RAID 5/6 isn't famous for write performance, but I want to make sure this is not an alignment issue.

From what I've heard, mdadm's 1.2 metadata format is advanced-format-safe, but I'm not sure about the effects of the LUKS encryption and the fact that I'm not using any partitions.

I've done some write performance testing:

single drive, single possibly aligned partition, no encryption: ~110MB/s (starting sector 40 but parted claims it's not aligned for optimal performance)
single drive, single aligned partition, no encryption: ~110MB/s (maybe VERY slightly faster than "possibly aligned")
single drive, single unaligned partition, no encryption: ~70-80MB/s (starting sector 37)

single drive, single aligned partition, encrypted: ~85-90MB/s
single drive, no partitions, encrypted: ~90-95MB/s

array of whole drives, default ext4, no encryption: ~55MB/s
array of whole drives, default ext4, encrypted: ~35MB/s
**array of whole drives, optimized ext4, encrypted: ~35MB/s** (mkfs.ext4 -t ext4 -j -b 4096 -m 0 -L Data -E stride=128,stripe-width=768 /dev/mapper/md2_crypt)

The bottommost line is my intended setup. RAID6 chunk size is 512kb.
 

So my question is: Is it normal for an encrypted RAID6 to be that slow?

---

