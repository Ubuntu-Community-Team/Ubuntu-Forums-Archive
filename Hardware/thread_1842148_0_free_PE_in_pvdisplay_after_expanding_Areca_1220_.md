---
title: "0 free PE in pvdisplay after expanding Areca 1220 RAID volume set"
date: 2011-09-10
forum: Hardware
---

### Post by mitnosirrag on 2011-09-10
Thanks ahead for any help.

My original setup was an Areca 1220 RAID card with (5) 2TB drives in RAID 5 with a hot spare, making only 4 of them part of the array for a total of 6TB.  I then created an LVM2 volume and mounted it as /storage (my root is a separate drive).  I formated the LVM2 volume as EXT4.

A few days ago, I hooked up another 2TB (exact same model) drive, the card found it, I was able to initialize it (actually had to set it to 7999GB for some silly reason) and was able to expand my RAID volume just fine.

I found this guy: [http://causton.net/areca.shtml](http://causton.net/areca.shtml) had a nearly identical setup, so I tried following his instructions, but when I get to `pvdisplay` it still says there is only the original amount of space available.  Here is the output of pvdisplay:

  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               grp0
  PV Size               5.46 TiB / not usable 3.81 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              1430510
  Free PE               0
  Allocated PE          1430510
  PV UUID               n3Jzyl-nWUw-lKGC-KiJb-7yUu-3jkI-GOOytf

So you can see there is 0 free PE when, to my understanding, there should be some.

I also found other people who had similar issues on various forums, including this one, but none of their advice helped either, and I actually got to the point where I couldn't mount the volume anymore, but was able to revert back to before I goofed.

I have tried rebooting, upgrading the RAID firmware, manually setting the PE size, and even seeing if the file system would increase automagically, nothing worked.  Another fun thing, `parted` (and `gparted`) show 8TB available, but says that it cannot manage LVM partions, so no apparent luck there.

For good measure, here is `lvdisplay`:

  --- Logical volume ---
  LV Name                /dev/grp0/vol0
  VG Name                grp0
  LV UUID                cQ2Eqv-qMDV-xa7D-cMLA-EU1i-3pKg-iJQ9gz
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                5.46 TiB
  Current LE             1430510
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0

And `vgdisplay`:

  --- Volume group ---
  VG Name               grp0
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  18
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               5.46 TiB
  PE Size               4.00 MiB
  Total PE              1430510
  Alloc PE / Size       1430510 / 5.46 TiB
  Free  PE / Size       0 / 0   
  VG UUID               zqKhpV-j7fi-IeIU-A4aV-0fDo-YWHF-C5M0il

Also, `parted`:

Model: Areca ARC-1220-VOL#00 (scsi)
Disk /dev/sdb: 7999GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  6000GB  6000GB                     lvm

And another strange thing, when I run `pvscan` I get this, and I don't get why:

  PV /dev/sdb1   VG grp0   lvm2 [5.46 TiB / 0    free]
  Total: 1 [1.46 TiB] / in use: 1 [1.46 TiB] / in no VG: 0 [0   ]

If there is anything else I can provide, please let me know.

Thanks

---

