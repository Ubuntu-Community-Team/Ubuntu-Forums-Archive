---
title: "Lacie Cloudbox RAID rescue"
date: 2019-03-05
forum: Hardware
---

### Post by mattpi78 on 2019-03-05
Hello,

I am fairly new to linux and have a major data recovery issue. I had a  3TB Lacie cloudbox drive that died on me a few weeks ago. It has a lot  of data that I am  trying  to recover.

I am trying to mount the raid array (2.7TB on sdc8) using mdadm. But I  am stuck. I am detailing my steps below. Hoping  an expert can help.

----------------------------------------------------------------------------------------------------------------------

sudo fdisk -l /dev/sdc
The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 48EB39C7-FA39-4315-9B4C-B7E4FE438E83

Device       Start        End    Sectors  Size Type
/dev/sdc1     2048       4095       2048    1M BIOS boot
/dev/sdc2     4096     397311     393216  192M Linux filesystem
/dev/sdc3   397312     399359       2048    1M Linux filesystem
/dev/sdc4   399360    3545087    3145728  1.5G Linux RAID
/dev/sdc5  3545088    6690815    3145728  1.5G Linux RAID
/dev/sdc6  6690816    8787967    2097152    1G Linux RAID
/dev/sdc7  8787968    9312255     524288  256M Linux RAID
/dev/sdc8  9312256 5860533134 5851220879  2.7T Linux RAID

----------------------------------------------------------------------------------------------------------------------

 sudo mdadm --examine /dev/sdc8
/dev/sdc8:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : 4467b8a4:e0a5ee80:898375b2:0fa2c83c
           Name : LaCie-CloudBox:8
  Creation Time : Thu Dec 31 18:00:15 2009
     Raid Level : raid1
   Raid Devices : 1

 Avail Dev Size : 5851220600 (2790.08 GiB 2995.82 GB)
     Array Size : 2925610300 (2790.08 GiB 2995.82 GB)
   Super Offset : 5851220856 sectors
   Unused Space : before=0 sectors, after=256 sectors
          State : clean
    Device UUID : a532e462:aff1e2de:beb5e05f:ccf88de8

    Update Time : Sun Mar  3 21:38:03 2019
       Checksum : 566c4bc8 - correct
         Events : 2


   Device Role : Active device 0
   Array State : A ('A' == active, '.' == missing, 'R' == replacing)

----------------------------------------------------------------------------------------------------------------------

 sudo mdadm --assemble --run /dev/md0 /dev/sdc8
mdadm: Found some drive for an array that is already active: /dev/md/LaCie-CloudBox:8
mdadm: giving up.

----------------------------------------------------------------------------------------------------------------------

What am I doing wrong? What should I do to mount sdc8 so that I can recover data?

Thank you.
Matt

---

