---
title: "Partitions not in /dev"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by ScarletEmerald on 2009-10-31
I have 3 SATA drives with these partitions

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10821    86919651    7  HPFS/NTFS
/dev/sda2           10822       30401   157276350   83  Linux

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   83  Linux
/dev/sdb2              14         379     2939895   83  Linux
/dev/sdb3             380        2812    19543072+  83  Linux
/dev/sdb4            2813       19457   133700962+  83  Linux

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux

```

But when I look in /dev I see

```

$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sdb  /dev/sdc  /dev/sdd

```

Where are the partitions on sdb and sdc?  I'm 90% sure they were there before I upgraded to Karmic.  Also, I have

```

$ ls /dev/mapper
control          nvidia_efadbaia1  nvidia_efadbaia3
nvidia_efadbaia  nvidia_efadbaia2  nvidia_efadbaia4

```

which seem to correspond to the sdb partitions.  I don't know how they got there, or why the sdc partition isn't there (or sda, for that matter).

---

### Post by diesch on 2009-10-31
What does
```
devkit-disks --dump
```
print?

---

### Post by ScarletEmerald on 2009-10-31
```

$ devkit-disks --dump
========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/dm_2d0
  native-path:                 /sys/devices/virtual/block/dm-0
  device:                      252:0
  device-file:                 /dev/mapper/nvidia_efadbaia
    by-id:                     /dev/disk/by-id/dm-name-nvidia_efadbaia
    by-id:                     /dev/disk/by-id/dm-uuid-DMRAID-nvidia_efadbaia
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Sat 31 Oct 2009 04:56:28 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       1
  presentation name:           
  presentation icon:           
  size:                        160041884672
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition table:
    scheme:                    mbr
    count:                     0
  drive:
    vendor:                    
    model:                     
    revision:                  
    serial:                    
    detachable:                0
    can spindown:              0
    rotational media:          1
    ejectable:                 0
    media:                     
      compat:                 
    interface:                 (unknown)
    if speed:                  (unknown)
    ATA SMART:                 not available

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/dm_2d1
  native-path:                 /sys/devices/virtual/block/dm-1
  device:                      252:1
  device-file:                 /dev/mapper/nvidia_efadbaia1
    by-id:                     /dev/disk/by-id/dm-name-nvidia_efadbaia1
    by-id:                     /dev/disk/by-id/dm-uuid-DMRAID-nvidia_efadbaia1
    by-id:                     /dev/disk/by-uuid/cccaf11d-47fe-479d-9219-01a9f6da1460
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Sat 31 Oct 2009 04:56:28 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  1
  mount paths:             /boot
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       1
  presentation name:           
  presentation icon:           
  size:                        106896384
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ext3
  version:                     1.0
  uuid:                        cccaf11d-47fe-479d-9219-01a9f6da1460
  label:                       
  drive:
    vendor:                    
    model:                     
    revision:                  
    serial:                    
    detachable:                0
    can spindown:              0
    rotational media:          1
    ejectable:                 0
    media:                     
      compat:                 
    interface:                 (unknown)
    if speed:                  (unknown)
    ATA SMART:                 not available

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/dm_2d2
  native-path:                 /sys/devices/virtual/block/dm-2
  device:                      252:2
  device-file:                 /dev/mapper/nvidia_efadbaia2
    by-id:                     /dev/disk/by-id/dm-name-nvidia_efadbaia2
    by-id:                     /dev/disk/by-id/dm-uuid-DMRAID-nvidia_efadbaia2
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Sat 31 Oct 2009 04:56:28 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       1
  presentation name:           
  presentation icon:           
  size:                        3010452480
  block size:                  512
  job underway:                no
  usage:                       raid
  type:                        LVM2_member
  version:                     LVM2\x20001
  uuid:                        QerYdp-kKlN-98kH-r2Sn-pu5L-zllw-Wk3Db1
  label:                       
  drive:
    vendor:                    
    model:                     
    revision:                  
    serial:                    
    detachable:                0
    can spindown:              0
    rotational media:          1
    ejectable:                 0
    media:                     
      compat:                 
    interface:                 (unknown)
    if speed:                  (unknown)
    ATA SMART:                 not available

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/dm_2d3
  native-path:                 /sys/devices/virtual/block/dm-3
  device:                      252:3
  device-file:                 /dev/mapper/nvidia_efadbaia3
    by-id:                     /dev/disk/by-id/dm-name-nvidia_efadbaia3
    by-id:                     /dev/disk/by-id/dm-uuid-DMRAID-nvidia_efadbaia3
    by-id:                     /dev/disk/by-uuid/c50f3eee-f8d5-4db6-b6ee-6fca240c2480
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Sat 31 Oct 2009 04:56:28 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  1
  mount paths:             /
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       1
  presentation name:           
  presentation icon:           
  size:                        20012106240
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ext3
  version:                     1.0
  uuid:                        c50f3eee-f8d5-4db6-b6ee-6fca240c2480
  label:                       
  drive:
    vendor:                    
    model:                     
    revision:                  
    serial:                    
    detachable:                0
    can spindown:              0
    rotational media:          1
    ejectable:                 0
    media:                     
      compat:                 
    interface:                 (unknown)
    if speed:                  (unknown)
    ATA SMART:                 not available

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/dm_2d4
  native-path:                 /sys/devices/virtual/block/dm-4
  device:                      252:4
  device-file:                 /dev/mapper/nvidia_efadbaia4
    by-id:                     /dev/disk/by-id/dm-name-nvidia_efadbaia4
    by-id:                     /dev/disk/by-id/dm-uuid-DMRAID-nvidia_efadbaia4
    by-id:                     /dev/disk/by-uuid/02d36e6b-7524-4612-980f-d5b9590102be
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Sat 31 Oct 2009 04:56:28 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  1
  mount paths:             /home
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       1
  presentation name:           
  presentation icon:           
  size:                        136909785600
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ext3
  version:                     1.0
  uuid:                        02d36e6b-7524-4612-980f-d5b9590102be
  label:                       
  drive:
    vendor:                    
    model:                     
    revision:                  
    serial:                    
    detachable:                0
    can spindown:              0
    rotational media:          1
    ejectable:                 0
    media:                     
      compat:                 
    interface:                 (unknown)
    if speed:                  (unknown)
    ATA SMART:                 not available

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/fd0
  native-path:                 /sys/devices/platform/floppy.0/block/fd0
  device:                      2:0
  device-file:                 /dev/fd0
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             0
  removable:                   1
  has media:                   0
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       1
  presentation name:           
  presentation icon:           
  size:                        0
  block size:                  0
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  drive:
    vendor:                    Floppy Drive
    model:                     
    revision:                  
    serial:                    
    detachable:                0
    can spindown:              0
    rotational media:          1
    ejectable:                 0
    media:                     
      compat:                  floppy
    interface:                 platform
    if speed:                  (unknown)
    ATA SMART:                 not available

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sda
  native-path:                 /sys/devices/pci0000:00/0000:00:07.0/host0/target0:0:0/0:0:0:0/block/sda
  device:                      8:0
  device-file:                 /dev/sda
    by-id:                     /dev/disk/by-id/ata-ST3250823AS_5ND2AL6V
    by-id:                     /dev/disk/by-id/scsi-SATA_ST3250823AS_5ND2AL6V
    by-path:                   /dev/disk/by-path/pci-0000:00:07.0-scsi-0:0:0:0
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Sat 31 Oct 2009 04:56:28 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        250059350016
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition table:
    scheme:                    mbr
    count:                     2
  drive:
    vendor:                    ATA
    model:                     ST3250823AS
    revision:                  3.03
    serial:                    5ND2AL6V
    detachable:                0
    can spindown:              1
    rotational media:          1
    ejectable:                 0
    media:                     
      compat:                 
    interface:                 ata
    if speed:                  (unknown)
    ATA SMART:                 Updated at Sat 31 Oct 2009 06:56:29 PM EDT
      overall assessment:      Good
===============================================================================
 Attribute       Current|Worst|Threshold  Status   Value       Type     Updates
===============================================================================
 raw-read-error-rate          48| 45|  6   good    143254983   Pre-fail Online 
 spin-up-time                 98| 98|  0    n/a    0           Pre-fail Online 
 start-stop-count            100|100| 20   good    193         Old-age  Online 
 reallocated-sector-count    100|100| 36   good    0 sectors   Pre-fail Online 
 seek-error-rate              88| 60| 30   good    716929893   Pre-fail Online 
 power-on-hours               68| 68|  0    n/a    1179.1 days Old-age  Online 
 spin-retry-count            100|100| 97   good    0           Pre-fail Online 
 power-cycle-count           100|100| 20   good    201         Old-age  Online 
 temperature-celsius-2        35| 42|  0    n/a    35C / 95F   Old-age  Online 
 hardware-ecc-recovered       48| 45|  0    n/a    143254983   Old-age  Online 
 current-pending-sector      100|100|  0    n/a    0 sectors   Old-age  Online 
 offline-uncorrectable       100|100|  0    n/a    0 sectors   Old-age  Offline
 udma-crc-error-count        200|199|  0    n/a    1           Old-age  Online 
 multi-zone-error-rate       100|253|  0    n/a    0           Old-age  Offline
 ta-increase-count           100|253|  0    n/a    0           Old-age  Online 

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sda1
  native-path:                 /sys/devices/pci0000:00/0000:00:07.0/host0/target0:0:0/0:0:0:0/block/sda/sda1
  device:                      8:1
  device-file:                 /dev/sda1
    by-id:                     /dev/disk/by-id/ata-ST3250823AS_5ND2AL6V-part1
    by-id:                     /dev/disk/by-id/scsi-SATA_ST3250823AS_5ND2AL6V-part1
    by-id:                     /dev/disk/by-uuid/3228CF3228CEF43F
    by-path:                   /dev/disk/by-path/pci-0000:00:07.0-scsi-0:0:0:0-part1
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Sat 31 Oct 2009 04:56:28 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  1
  mount paths:             /mnt/sda1
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        89005722624
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ntfs
  version:                     
  uuid:                        3228CF3228CEF43F
  label:                       
  partition:
    part of:                   /org/freedesktop/DeviceKit/Disks/devices/sda
    scheme:                    mbr
    number:                    1
    type:                      0x07
    flags:                 boot
    offset:                    32256
    size:                      89005722624
    label:                     
    uuid:                      

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sda2
  native-path:                 /sys/devices/pci0000:00/0000:00:07.0/host0/target0:0:0/0:0:0:0/block/sda/sda2
  device:                      8:2
  device-file:                 /dev/sda2
    by-id:                     /dev/disk/by-id/ata-ST3250823AS_5ND2AL6V-part2
    by-id:                     /dev/disk/by-id/scsi-SATA_ST3250823AS_5ND2AL6V-part2
    by-path:                   /dev/disk/by-path/pci-0000:00:07.0-scsi-0:0:0:0-part2
  detected at:                 Sat 31 Oct 2009 06:07:32 PM EDT
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Sat 31 Oct 2009 06:07:32 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        161050982400
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition:
    part of:                   /org/freedesktop/DeviceKit/Disks/devices/sda
    scheme:                    mbr
    number:                    2
    type:                      0x83
    flags:                
    offset:                    89005754880
    size:                      161050982400
    label:                     
    uuid:                      

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sdb
  native-path:                 /sys/devices/pci0000:00/0000:00:08.0/host2/target2:0:0/2:0:0:0/block/sdb
  device:                      8:16
  device-file:                 /dev/sdb
    by-id:                     /dev/disk/by-id/ata-ST3160023AS_3JS33NDS
    by-id:                     /dev/disk/by-id/scsi-SATA_ST3160023AS_3JS33NDS
    by-path:                   /dev/disk/by-path/pci-0000:00:08.0-scsi-0:0:0:0
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Sat 31 Oct 2009 04:56:28 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        160041885696
  block size:                  512
  job underway:                no
  usage:                       raid
  type:                        nvidia_raid_member
  version:                     100
  uuid:                        
  label:                       
  partition table:
    scheme:                    mbr
    count:                     0
  drive:
    vendor:                    ATA
    model:                     ST3160023AS
    revision:                  3.18
    serial:                    3JS33NDS
    detachable:                0
    can spindown:              1
    rotational media:          1
    ejectable:                 0
    media:                     
      compat:                 
    interface:                 ata
    if speed:                  (unknown)
    ATA SMART:                 Updated at Sat 31 Oct 2009 06:56:29 PM EDT
      overall assessment:      Disk has a few bad sectors
===============================================================================
 Attribute       Current|Worst|Threshold  Status   Value       Type     Updates
===============================================================================
 raw-read-error-rate          59| 52|  6   good    52027543    Pre-fail Online 
 spin-up-time                 97| 96|  0    n/a    0           Pre-fail Online 
 start-stop-count            100|100| 20   good    139         Old-age  Online 
 reallocated-sector-count    100|100| 36   good    1 sectors   Pre-fail Online 
 seek-error-rate              88| 60| 30   good    700991102   Pre-fail Online 
 power-on-hours               78| 78|  0    n/a    807.8 days  Old-age  Online 
 spin-retry-count            100|100| 97   good    0           Pre-fail Online 
 power-cycle-count           100|100| 20   good    248         Old-age  Online 
 temperature-celsius-2        37| 46|  0    n/a    37C / 98.6F Old-age  Online 
 hardware-ecc-recovered       59| 52|  0    n/a    52027543    Old-age  Online 
 current-pending-sector      100|100|  0    n/a    23 sectors  Old-age  Online 
 offline-uncorrectable       100|100|  0    n/a    23 sectors  Old-age  Offline
 udma-crc-error-count        200|199|  0    n/a    2           Old-age  Online 
 multi-zone-error-rate       100|253|  0    n/a    0           Old-age  Offline
 ta-increase-count           100|253|  0    n/a    0           Old-age  Online 

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sdc
  native-path:                 /sys/devices/pci0000:00/0000:00:08.0/host3/target3:0:0/3:0:0:0/block/sdc
  device:                      8:32
  device-file:                 /dev/sdc
    by-id:                     /dev/disk/by-id/ata-ST3160023AS_3JS33M69
    by-id:                     /dev/disk/by-id/scsi-SATA_ST3160023AS_3JS33M69
    by-path:                   /dev/disk/by-path/pci-0000:00:08.0-scsi-1:0:0:0
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Sat 31 Oct 2009 04:56:28 PM EDT)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        160041885696
  block size:                  512
  job underway:                no
  usage:                       raid
  type:                        nvidia_raid_member
  version:                     100
  uuid:                        
  label:                       
  partition table:
    scheme:                    mbr
    count:                     0
  drive:
    vendor:                    ATA
    model:                     ST3160023AS
    revision:                  3.18
    serial:                    3JS33M69
    detachable:                0
    can spindown:              1
    rotational media:          1
    ejectable:                 0
    media:                     
      compat:                 
    interface:                 ata
    if speed:                  (unknown)
    ATA SMART:                 Updated at Sat 31 Oct 2009 06:56:29 PM EDT
      overall assessment:      Good
===============================================================================
 Attribute       Current|Worst|Threshold  Status   Value       Type     Updates
===============================================================================
 raw-read-error-rate          64| 56|  6   good    94714599    Pre-fail Online 
 spin-up-time                 97| 96|  0    n/a    0           Pre-fail Online 
 start-stop-count            100|100| 20   good    133         Old-age  Online 
 reallocated-sector-count    100|100| 36   good    0 sectors   Pre-fail Online 
 seek-error-rate              89| 60| 30   good    822438111   Pre-fail Online 
 power-on-hours               66| 66|  0    n/a    1264.9 days Old-age  Online 
 spin-retry-count            100|100| 97   good    0           Pre-fail Online 
 power-cycle-count           100|100| 20   good    247         Old-age  Online 
 temperature-celsius-2        38| 47|  0    n/a    38C / 100F  Old-age  Online 
 hardware-ecc-recovered       64| 56|  0    n/a    94714599    Old-age  Online 
 current-pending-sector      100|100|  0    n/a    0 sectors   Old-age  Online 
 offline-uncorrectable       100|100|  0    n/a    0 sectors   Old-age  Offline
 udma-crc-error-count        200|199|  0    n/a    1           Old-age  Online 
 multi-zone-error-rate       100|253|  0    n/a    0           Old-age  Offline
 ta-increase-count           100|253|  0    n/a    0           Old-age  Online 

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sdd
  native-path:                 /sys/devices/pci0000:00/0000:00:06.0/host4/target4:0:1/4:0:1:0/block/sdd
  device:                      8:48
  device-file:                 /dev/sdd
    by-path:                   /dev/disk/by-path/pci-0000:00:06.0-scsi-0:0:1:0
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             0
  removable:                   1
  has media:                   0
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        0
  block size:                  0
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  drive:
    vendor:                    IOMEGA
    model:                     ZIP 250
    revision:                  42.S
    serial:                    
    detachable:                0
    can spindown:              0
    rotational media:          1
    ejectable:                 1
    media:                     
      compat:                  floppy_zip
    interface:                 scsi
    if speed:                  (unknown)
    ATA SMART:                 not available

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sr0
  native-path:                 /sys/devices/pci0000:00/0000:00:06.0/host4/target4:0:0/4:0:0:0/block/sr0
  device:                      11:0
  device-file:                 /dev/sr0
    by-path:                   /dev/disk/by-path/pci-0000:00:06.0-scsi-0:0:0:0
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             0
  removable:                   1
  has media:                   0
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        0
  block size:                  0
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  drive:
    vendor:                    LITE-ON
    model:                     DVDRW LH-20A1H
    revision:                  LL06
    serial:                    
    detachable:                0
    can spindown:              0
    rotational media:          1
    ejectable:                 1
    media:                     
      compat:                  optical_cd optical_cd_r optical_cd_rw optical_dvd optical_dvd_r optical_dvd_ram optical_mrw optical_mrw_w
    interface:                 scsi
    if speed:                  (unknown)
    ATA SMART:                 not available

========================================================================
Showing information for /org/freedesktop/DeviceKit/Disks/devices/sr1
  native-path:                 /sys/devices/pci0000:00/0000:00:06.0/host5/target5:0:1/5:0:1:0/block/sr1
  device:                      11:1
  device-file:                 /dev/sr1
    by-path:                   /dev/disk/by-path/pci-0000:00:06.0-scsi-1:0:1:0
  detected at:                 Sat 31 Oct 2009 04:56:28 PM EDT
  system internal:             0
  removable:                   1
  has media:                   1 (detected at Sat 31 Oct 2009 04:56:28 PM EDT)
    detects change:            1
    detection by polling:      1
    detection inhibitable:     1
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        4559241216
  block size:                  2048
  job underway:                no
  usage:                       filesystem
  type:                        iso9660
  version:                     Joliet\x20Extension
  uuid:                        
  label:                       AVS
  optical disc:
    blank:                     1
    appendable:                0
    closed:                    0
    num tracks:                192
    num audio tracks:          0
    num sessions:              23628
  drive:
    vendor:                    PIONEER
    model:                     DVD-ROM DVD-115F
    revision:                  1.27
    serial:                    
    detachable:                0
    can spindown:              0
    rotational media:          1
    ejectable:                 1
    media:                     optical_dvd
      compat:                  optical_cd optical_dvd optical_mrw optical_mrw_w
    interface:                 scsi
    if speed:                  (unknown)
    ATA SMART:                 not available

========================================================================

```

---

### Post by diesch on 2009-10-31
According to that the following disks are there:

                 /dev/mapper/nvidia_efadbaia    RAID   
                 /dev/mapper/nvidia_efadbaia1  mounted at /boot
                 /dev/mapper/nvidia_efadbaia2  LVM2
                 /dev/mapper/nvidia_efadbaia3  mounted at /
                 /dev/mapper/nvidia_efadbaia4  mounted at /home
                 /dev/sda  disc
                 /dev/sda1 mounted at /mnt/sda1
                 /dev/sda2  
                 /dev/sdb  RAID, disk has a few bad sectors
                 /dev/sdc  RAID
                 /dev/sdd  IOMEGA ZIP

I guess /dev/mapper/nvidia* are the former /dev/sdb*, /dev/sdb is your former /dev/sdc, sdb1 (the former sdc1) isn't there because the disk damaged.

The current sdc is the same model as sdb (ST3160023AS) but has another serial number.

---

### Post by ScarletEmerald on 2009-10-31
That seems plausible- I was playing with RAID a few years ago, and there may have been some remnants that got picked up when I did the upgrade.  Guess I'll see if I can disable that in bios or something.

---

### Post by diesch on 2009-10-31
You should prepare yourself to replace the disc with the bad sectors as it's likely to die in the near future

---

### Post by ScarletEmerald on 2009-10-31
That was it- I removed dmraid and my devices came back.  Thanks for the warning about the bad sectors.

---

### Post by darkod on 2009-11-15
A friend has similar problem. He has only one drive but it is reported as nvidia_raid_meber don't know why, probably leftovers.
How did you solve this, is it just removing raid in BIOS? Is the data on the disk at risk?
Thanks.

---

### Post by ScarletEmerald on 2009-11-15
Removing the RAID in the BIOS didn't fix it, I had to uninstall the dmraid program.  The data that was on the drive was still there after it was out of the RAID.

---

