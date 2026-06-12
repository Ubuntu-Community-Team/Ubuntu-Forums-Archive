---
title: "Raid-trouble: &quot;Invalid RAID superblock&quot;"
date: 2009-09-03
forum: Hardware
---

### Post by ZippZapp on 2009-09-03
Hello!

I have serious trouble with my Ubuntu server after a series of power-outages during a few minutes.

I have tried to run Testdisk which reports:
---------------------------------------------------------------
 TestDisk 6.8, Data Recovery Utility, August 2007
 Christophe GRENIER <grenier@cgsecurity.org>
 [http://www.cgsecurity.org](http://www.cgsecurity.org)
 Please wait...
 Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63, sector  size=512
 Disk /dev/sdb - 320 GB / 298 GiB - CHS 38913 255 63, sector  size=512

 Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
      Partition			Start        End    Size in  sectors
 Invalid RAID superblock
  1 * Linux RAID               0   1  1 38296 254 63  615241242
  1 * Linux RAID               0   1  1 38296 254 63  615241242
  2 P Linux Swap           38297   0  1 38912 254 63    9896040
 Disk /dev/sdb - 320 GB / 298 GiB - CHS 38913 255 63
      Partition			Start        End    Size in  sectors
 Invalid RAID superblock
  1 * Linux RAID               0   1  1 38296 254 63  615241242
  1 * Linux RAID               0   1  1 38296 254 63  615241242
  2 P Linux Swap           38297   0  1 38912 254 63    9896040
----------------------------------------------------------------

**How do I fix the "Invalid RAID superblock" problem?**
The two identical disks should be mirrored.

After power-up it does not always boot. Sometimes it hangs, sometimes I get the grub-prompt and sometimes it starts just fine.

---

