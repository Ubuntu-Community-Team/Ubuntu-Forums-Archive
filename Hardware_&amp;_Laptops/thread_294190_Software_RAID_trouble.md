---
title: "Software RAID trouble"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by edeca on 2006-11-06
I recently installed an Ubuntu server with mirrored disks using software RAID.  After a kernel upgrade from apt to 2.6.15-27 I shutdown and everything worked fine until the next shutdown.  Now the machine will not boot because it appears the superblock is wrong on some of the RAID devices on the first disk.

The rough layout of the disks (sda and sdb):

sdx1 (md0) - /
sdx2 (md1) - /var
sdx3 (md2) - /usr
extended partition with swap
sdx6 (md3) - /opt

The exact error is:

"invalid superblock checksum on sda3
sda3 has invalid sb, not importing!"

Booting into the Ubuntu install CD and using the terminal, mdadm -E /dev/sdaX shows that the checksum is not what would be expected for sda1,2,3 but is fine for sda6.  All of the checksums on drive sdb are correct.

The state is "clean" for all partitions, working 2, active 2 and failed 0.  The table for sdb1,2,3 shows that the first device has been removed and is no longer an active mirror.

What is the best way to proceed here?  Can I somehow sync from the second disk, which appears to have the correct checksums?  Is there an easy way to fix this that wont involve loosing the data?

---

