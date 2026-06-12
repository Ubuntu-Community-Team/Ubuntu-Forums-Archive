---
title: "Help! One of my raid partitions has disappeared."
date: 2015-04-30
forum: Hardware
---

### Post by jqnathan on 2015-04-30
Hi!
First time posting but I can't solve this by my self, so pleas help me. :)
I have a problem, I can't access one of my partitions. 
I have three 2 TB disks that are running hardware raid5, and on that there are two 2 TB "partitions". When I boot my computer the Raid screen says that everything is working. But when in ubuntu I only find one of the partitions. It has worked before and I'm not sure but I think it stopped working when i upgraded to 14.04.

This should be the three physical disks in Raid5:
/dev/sdb
/dev/sdd/
/dev/sde/

The one partition in raid I can access is called /dev/dm-1

I've tried mounting it like this /usr/bin/udisks --mount  /dev/disk/by-id/dm-uuid-DMRAID-isw_dafhbfdidg_Volume0Mount failed: One or more block devices are holding /dev/dm-0.

Here are some dumps that might be useful:
[HR][/HR]
This is the response from "sudo fdisk -lu"


Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x525b1087


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   232138751   116068352    7  HPFS/NTFS/exFAT
/dev/sda2       232138752  1248163839   508012544    7  HPFS/NTFS/exFAT
/dev/sda3      1248163840  1250260991     1048576    6  FAT16


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa6c91793


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3906990079  1953494016    7  HPFS/NTFS/exFAT


Disk /dev/sdc: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    15681535     7839744    7  HPFS/NTFS/exFAT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x7ced7cee


   Device Boot      Start         End      Blocks   Id  System


WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xda246b7d


Disk /dev/sde doesn't contain a valid partition table


Disk /dev/sdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e35c


   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *        2048   209281023   104639488   83  Linux
/dev/sdf2       209283070   234440703    12578817    5  Extended
/dev/sdf5       209283072   234440703    12578816   82  Linux swap / Solaris


Disk /dev/mapper/isw_dafhbfdidg_Volume0: 2000.4 GB, 2000381280256 bytes
255 heads, 63 sectors/track, 243199 cylinders, total 3906994688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0xa6c91793


                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dafhbfdidg_Volume0p1            2048  3906990079  1953494016    7  HPFS/NTFS/exFAT


Disk /dev/mapper/isw_dafhbfdidg_Volume0p1: 2000.4 GB, 2000377872384 bytes
255 heads, 63 sectors/track, 243198 cylinders, total 3906988032 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x6e697373


This doesn't look like a partition table
Probably you selected the wrong device.


                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_dafhbfdidg_Volume0p1p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_dafhbfdidg_Volume0p1p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_dafhbfdidg_Volume0p1p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_dafhbfdidg_Volume0p1p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.


Partition table entries are not in disk order

[HR][/HR]
And this is the output from "/usr/bin/udisks --dump":


[HR][/HR]========================================================================
Showing information for /org/freedesktop/UDisks/devices/dm_2d0
  native-path:                 /sys/devices/virtual/block/dm-0
  device:                      252:0
  device-file:                 /dev/dm-0
    presentation:              /dev/dm-0
    by-id:                     /dev/disk/by-id/dm-name-isw_dafhbfdidg_Volume0
    by-id:                     /dev/disk/by-id/dm-uuid-DMRAID-isw_dafhbfdidg_Volume0
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        2000381280256
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition table:
    scheme:                    mbr
    count:                     1
  drive:
    vendor:                    
    model:                     
    revision:                  
    serial:                    
    WWN:                       
    detachable:                0
    can spindown:              0
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 (unknown)
    if speed:                  (unknown)
    ATA SMART:                 not available


========================================================================
Showing information for /org/freedesktop/UDisks/devices/dm_2d1
  native-path:                 /sys/devices/virtual/block/dm-1
  device:                      252:1
  device-file:                 /dev/dm-1
    presentation:              /dev/dm-1
    by-id:                     /dev/disk/by-id/dm-name-isw_dafhbfdidg_Volume0p1
    by-id:                     /dev/disk/by-id/dm-uuid-part1-DMRAID-isw_dafhbfdidg_Volume0
    by-id:                     /dev/disk/by-id/raid-isw_dafhbfdidg_Volume0-part1
    by-id:                     /dev/disk/by-uuid/D88229DF8229C2BC
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  1
  mount paths:             /media/Disk1
  mounted by uid:              1000
  presentation hide:           0
  presentation nopolicy:       1
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        2000377872384
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ntfs
  version:                     
  uuid:                        D88229DF8229C2BC
  label:                       Disk1
  partition:
    part of:                   /org/freedesktop/UDisks/devices/dm_2d0
    scheme:                    mbr
    number:                    1
    type:                      0x07
    flags:                    
    offset:                    1048576
    alignment offset:          0
    size:                      2000377872384
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:0/2:0:0:0/block/sda
  device:                      8:0
  device-file:                 /dev/sda
    presentation:              /dev/sda
    by-id:                     /dev/disk/by-id/ata-SAMSUNG_HM640JJ_S2FTJ1LZA00289
    by-id:                     /dev/disk/by-id/wwn-0x50024e9004323f5f
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        640135028736
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition table:
    scheme:                    mbr
    count:                     3
  drive:
    vendor:                    ATA
    model:                     SAMSUNG HM640JJ
    revision:                  2AK10001
    serial:                    S2FTJ1LZA00289
    WWN:                       50024e9004323f5f
    detachable:                0
    can spindown:              1
    rotational media:          Yes, at 7200 RPM
    write-cache:               enabled
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 ata
    if speed:                  (unknown)
    ATA SMART:                 Updated at 2015-04-30T14:04:38 CEST
      overall assessment:      Disk has a few bad sectors
===============================================================================
 Attribute       Current|Worst|Threshold  Status   Value       Type     Updates
===============================================================================
 raw-read-error-rate         100|100| 51   good    8381        Pre-fail Online 
 throughput-performance      252|252|  0    n/a    0           Old-age  Online 
 spin-up-time                 89| 86| 25   good    3,6 secs    Pre-fail Online 
 start-stop-count             99| 99|  0    n/a    1950        Old-age  Online 
 reallocated-sector-count    252|252| 10   good    0 sectors   Pre-fail Online 
 seek-error-rate             252|252| 51   good    0           Old-age  Online 
 seek-time-performance       252|252| 15   good    0           Old-age  Offline
 power-on-hours              100|100|  0    n/a    230,6 days  Old-age  Online 
 spin-retry-count            252|252| 51   good    0           Old-age  Online 
 calibration-retry-count      99| 99|  0    n/a    1468        Old-age  Online 
 power-cycle-count            99| 99|  0    n/a    1021        Old-age  Online 
 g-sense-error-rate          100|100|  0    n/a    264         Old-age  Online 
 power-off-retract-count     252|252|  0    n/a    0           Old-age  Online 
 temperature-celsius-2        64| 55|  0    n/a    26C / 78,8F Old-age  Online 
 hardware-ecc-recovered      100|100|  0    n/a    0           Old-age  Online 
 reallocated-event-count     252|252|  0    n/a    0           Old-age  Online 
 current-pending-sector       98| 98|  0    n/a    230 sectors Old-age  Online 
 offline-uncorrectable       252|252|  0    n/a    0 sectors   Old-age  Offline
 udma-crc-error-count        100|100|  0    n/a    137         Old-age  Online 
 multi-zone-error-rate       100|100|  0    n/a    6           Old-age  Online 
 load-retry-count             99| 99|  0    n/a    1468        Old-age  Online 
 load-cycle-count-2           87| 87|  0    n/a    134444      Old-age  Online 


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda1
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:0/2:0:0:0/block/sda/sda1
  device:                      8:1
  device-file:                 /dev/sda1
    presentation:              /dev/sda1
    by-id:                     /dev/disk/by-id/ata-SAMSUNG_HM640JJ_S2FTJ1LZA00289-part1
    by-id:                     /dev/disk/by-id/wwn-0x50024e9004323f5f-part1
    by-id:                     /dev/disk/by-uuid/5E409FFE409FDADB
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        118853992448
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ntfs
  version:                     
  uuid:                        5E409FFE409FDADB
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    1
    type:                      0x07
    flags:                     boot
    offset:                    1048576
    alignment offset:          0
    size:                      118853992448
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda2
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:0/2:0:0:0/block/sda/sda2
  device:                      8:2
  device-file:                 /dev/sda2
    presentation:              /dev/sda2
    by-id:                     /dev/disk/by-id/ata-SAMSUNG_HM640JJ_S2FTJ1LZA00289-part2
    by-id:                     /dev/disk/by-id/wwn-0x50024e9004323f5f-part2
    by-id:                     /dev/disk/by-uuid/C09607D39607C93C
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        520204845056
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ntfs
  version:                     
  uuid:                        C09607D39607C93C
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    2
    type:                      0x07
    flags:                    
    offset:                    118855041024
    alignment offset:          0
    size:                      520204845056
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sda3
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata3/host2/target2:0:0/2:0:0:0/block/sda/sda3
  device:                      8:3
  device-file:                 /dev/sda3
    presentation:              /dev/sda3
    by-id:                     /dev/disk/by-id/ata-SAMSUNG_HM640JJ_S2FTJ1LZA00289-part3
    by-id:                     /dev/disk/by-id/wwn-0x50024e9004323f5f-part3
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        1073741824
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sda
    scheme:                    mbr
    number:                    3
    type:                      0x06
    flags:                    
    offset:                    639059886080
    alignment offset:          0
    size:                      1073741824
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdb
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata4/host3/target3:0:0/3:0:0:0/block/sdb
  device:                      8:16
  device-file:                 /dev/sdb
    presentation:              /dev/sdb
    by-id:                     /dev/disk/by-id/ata-WDC_WD20EARS-00MVWB0_WD-WMAZA2329196
    by-id:                     /dev/disk/by-id/wwn-0x50014ee600a3fd30
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        2000398934016
  block size:                  512
  job underway:                no
  usage:                       raid
  type:                        isw_raid_member
  version:                     1.2.02
  uuid:                        
  label:                       
  drive:
    vendor:                    ATA
    model:                     WDC WD20EARS-00MVWB0
    revision:                  51.0AB51
    serial:                    WD-WMAZA2329196
    WWN:                       50014ee600a3fd30
    detachable:                0
    can spindown:              1
    rotational media:          Yes, unknown rate
    write-cache:               enabled
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 ata
    if speed:                  (unknown)
    ATA SMART:                 Updated at 2015-04-30T14:04:37 CEST
      overall assessment:      Good
===============================================================================
 Attribute       Current|Worst|Threshold  Status   Value       Type     Updates
===============================================================================
 raw-read-error-rate         200|200| 51   good    0           Pre-fail Online 
 spin-up-time                253|167| 21   good    1,2 secs    Pre-fail Online 
 start-stop-count             98| 98|  0    n/a    2712        Old-age  Online 
 reallocated-sector-count    200|200|140   good    0 sectors   Pre-fail Online 
 seek-error-rate             200|200|  0    n/a    0           Old-age  Online 
 power-on-hours               87| 87|  0    n/a    411,5 days  Old-age  Online 
 spin-retry-count            100|100|  0    n/a    0           Old-age  Online 
 calibration-retry-count     100|100|  0    n/a    0           Old-age  Online 
 power-cycle-count            99| 99|  0    n/a    1166        Old-age  Online 
 power-off-retract-count     200|200|  0    n/a    237         Old-age  Online 
 load-cycle-count            176|176|  0    n/a    72145       Old-age  Online 
 temperature-celsius-2       121| 96|  0    n/a    29C / 84,2F Old-age  Online 
 reallocated-event-count     200|200|  0    n/a    0           Old-age  Online 
 current-pending-sector      200|200|  0    n/a    0 sectors   Old-age  Online 
 offline-uncorrectable       200|200|  0    n/a    0 sectors   Old-age  Offline
 udma-crc-error-count        200|200|  0    n/a    0           Old-age  Online 
 multi-zone-error-rate       200|200|  0    n/a    12          Old-age  Offline


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdc
  native-path:                 /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host16/target16:0:0/16:0:0:0/block/sdc
  device:                      8:32
  device-file:                 /dev/sdc
    presentation:              /dev/sdc
    by-id:                     /dev/disk/by-id/usb-SanDisk_Cruzer_077430189640FECF-0:0
    by-path:                   /dev/disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:0
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             0
  removable:                   1
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        8029470208
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition table:
    scheme:                    mbr
    count:                     1
  drive:
    vendor:                    SanDisk
    model:                     Cruzer
    revision:                  8.01
    serial:                    077430189640FECF
    WWN:                       
    detachable:                1
    can spindown:              0
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 usb
    if speed:                  480000000 bits/s
    ATA SMART:                 not available


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdc1
  native-path:                 /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host16/target16:0:0/16:0:0:0/block/sdc/sdc1
  device:                      8:33
  device-file:                 /dev/sdc1
    presentation:              /dev/sdc1
    by-id:                     /dev/disk/by-id/usb-SanDisk_Cruzer_077430189640FECF-0:0-part1
    by-id:                     /dev/disk/by-uuid/1C24055724053574
    by-path:                   /dev/disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:0-part1
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             0
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  1
  mount paths:             /media/jonathan/1C24055724053574
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        8027897856
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ntfs
  version:                     
  uuid:                        1C24055724053574
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sdc
    scheme:                    mbr
    number:                    1
    type:                      0x07
    flags:                     boot
    offset:                    1048576
    alignment offset:          0
    size:                      8027897856
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdd
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata5/host4/target4:0:0/4:0:0:0/block/sdd
  device:                      8:48
  device-file:                 /dev/sdd
    presentation:              /dev/sdd
    by-id:                     /dev/disk/by-id/ata-WDC_WD20EARX-00PASB0_WD-WMAZA7931755
    by-id:                     /dev/disk/by-id/wwn-0x50014ee25c25b249
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        2000398934016
  block size:                  512
  job underway:                no
  usage:                       raid
  type:                        isw_raid_member
  version:                     1.2.02
  uuid:                        
  label:                       
  drive:
    vendor:                    ATA
    model:                     WDC WD20EARX-00PASB0
    revision:                  51.0AB51
    serial:                    WD-WMAZA7931755
    WWN:                       50014ee25c25b249
    detachable:                0
    can spindown:              1
    rotational media:          Yes, unknown rate
    write-cache:               enabled
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 ata
    if speed:                  (unknown)
    ATA SMART:                 Updated at 2015-04-30T14:04:38 CEST
      overall assessment:      Good
===============================================================================
 Attribute       Current|Worst|Threshold  Status   Value       Type     Updates
===============================================================================
 raw-read-error-rate         200|200| 51   good    0           Pre-fail Online 
 spin-up-time                172|170| 21   good    6,4 secs    Pre-fail Online 
 start-stop-count             99| 99|  0    n/a    1817        Old-age  Online 
 reallocated-sector-count    200|200|140   good    0 sectors   Pre-fail Online 
 seek-error-rate             200|200|  0    n/a    0           Old-age  Online 
 power-on-hours               91| 91|  0    n/a    290,8 days  Old-age  Online 
 spin-retry-count            100|100|  0    n/a    0           Old-age  Online 
 calibration-retry-count     100|100|  0    n/a    0           Old-age  Online 
 power-cycle-count           100|100|  0    n/a    657         Old-age  Online 
 power-off-retract-count     200|200|  0    n/a    67          Old-age  Online 
 load-cycle-count            182|182|  0    n/a    56899       Old-age  Online 
 temperature-celsius-2       123|108|  0    n/a    27C / 80,6F Old-age  Online 
 reallocated-event-count     200|200|  0    n/a    0           Old-age  Online 
 current-pending-sector      200|200|  0    n/a    0 sectors   Old-age  Online 
 offline-uncorrectable       200|200|  0    n/a    0 sectors   Old-age  Offline
 udma-crc-error-count        200|200|  0    n/a    0           Old-age  Online 
 multi-zone-error-rate       200|200|  0    n/a    177         Old-age  Offline


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sde
  native-path:                 /sys/devices/pci0000:00/0000:00:1f.2/ata6/host5/target5:0:0/5:0:0:0/block/sde
  device:                      8:64
  device-file:                 /dev/sde
    presentation:              /dev/sde
    by-id:                     /dev/disk/by-id/ata-WDC_WD20EARS-00MVWB0_WD-WMAZA2346429
    by-id:                     /dev/disk/by-id/wwn-0x50014ee655f95d10
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        2000398934016
  block size:                  512
  job underway:                no
  usage:                       raid
  type:                        isw_raid_member
  version:                     1.2.02
  uuid:                        
  label:                       
  drive:
    vendor:                    ATA
    model:                     WDC WD20EARS-00MVWB0
    revision:                  51.0AB51
    serial:                    WD-WMAZA2346429
    WWN:                       50014ee655f95d10
    detachable:                0
    can spindown:              1
    rotational media:          Yes, unknown rate
    write-cache:               enabled
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 ata
    if speed:                  (unknown)
    ATA SMART:                 Updated at 2015-04-30T14:04:38 CEST
      overall assessment:      Good
===============================================================================
 Attribute       Current|Worst|Threshold  Status   Value       Type     Updates
===============================================================================
 raw-read-error-rate         200|200| 51   good    0           Pre-fail Online 
 spin-up-time                253|168| 21   good    1,1 secs    Pre-fail Online 
 start-stop-count             98| 98|  0    n/a    2711        Old-age  Online 
 reallocated-sector-count    200|200|140   good    0 sectors   Pre-fail Online 
 seek-error-rate             200|200|  0    n/a    0           Old-age  Online 
 power-on-hours               87| 87|  0    n/a    411,4 days  Old-age  Online 
 spin-retry-count            100|100|  0    n/a    0           Old-age  Online 
 calibration-retry-count     100|100|  0    n/a    0           Old-age  Online 
 power-cycle-count            99| 99|  0    n/a    1167        Old-age  Online 
 power-off-retract-count     200|200|  0    n/a    239         Old-age  Online 
 load-cycle-count            177|177|  0    n/a    70961       Old-age  Online 
 temperature-celsius-2       123| 97|  0    n/a    27C / 80,6F Old-age  Online 
 reallocated-event-count     200|200|  0    n/a    0           Old-age  Online 
 current-pending-sector      200|200|  0    n/a    0 sectors   Old-age  Online 
 offline-uncorrectable       200|200|  0    n/a    0 sectors   Old-age  Offline
 udma-crc-error-count        200|200|  0    n/a    0           Old-age  Online 
 multi-zone-error-rate       200|200|  0    n/a    0           Old-age  Offline


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdf
  native-path:                 /sys/devices/pci0000:00/0000:00:01.0/0000:02:00.0/ata10/host9/target9:0:0/9:0:0:0/block/sdf
  device:                      8:80
  device-file:                 /dev/sdf
    presentation:              /dev/sdf
    by-id:                     /dev/disk/by-id/ata-OCZ-AGILITY3_OCZ-3AV443TY6S6AUMO0
    by-id:                     /dev/disk/by-id/wwn-0x5e83a97ee0aa19e8
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        120034123776
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition table:
    scheme:                    mbr
    count:                     3
  drive:
    vendor:                    ATA
    model:                     OCZ-AGILITY3
    revision:                  2.15
    serial:                    OCZ-3AV443TY6S6AUMO0
    WWN:                       5e83a97ee0aa19e8
    detachable:                0
    can spindown:              1
    rotational media:          No
    write-cache:               enabled
    ejectable:                 0
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                 
    interface:                 ata
    if speed:                  (unknown)
    ATA SMART:                 Updated at 2015-04-30T14:04:37 CEST
      overall assessment:      Good
===============================================================================
 Attribute       Current|Worst|Threshold  Status   Value       Type     Updates
===============================================================================
 raw-read-error-rate          90| 90| 50   good    7820663     Pre-fail Online 
 reallocated-sector-count    100|100|  3   good    0 sectors   Pre-fail Online 
 power-on-hours               90| 90|  0    n/a    373,2 days  Old-age  Online 
 power-cycle-count           100|100|  0    n/a    745         Old-age  Online 
 program-fail-count          n/a|n/a|  0    n/a    0           Old-age  Online 
 erase-fail-count            n/a|n/a|  0    n/a    0           Old-age  Online 
 attribute-174               n/a|n/a|  0    n/a    0           Old-age  Offline
 wear-leveling-count         n/a|n/a|  0    n/a    3           Old-age  Offline
 program-fail-count-total    n/a|n/a|  0    n/a    0           Old-age  Online 
 erase-fail-count-total      n/a|n/a|  0    n/a    0           Old-age  Online 
 reported-uncorrect          100|100|  0    n/a    0 sectors   Old-age  Online 
 temperature-celsius-2        30| 30|  0    n/a    30C / 86F   Old-age  Online 
 hardware-ecc-recovered      120|120|  0    n/a    7820663     Old-age  Offline
 reallocated-event-count     100|100|  3   good    0           Pre-fail Online 
 soft-read-error-rate        120|120|  0    n/a    7820663     Old-age  Offline
 shock-count-write-open      120|120|  0    n/a    7820663     Old-age  Offline
 head-amplitude              100|100|  0    n/a    0           Pre-fail Online 
 temperature-celsius         100|100| 10   good    0C / 32F    Pre-fail Online 
 power-on-seconds-2          n/a|n/a|  0    n/a    0           Old-age  Offline
 uncorrectable-ecc-count     n/a|n/a|  0    n/a    3904 sectors Old-age  Online 
 total-lbas-written          n/a|n/a|  0    n/a    130996      Old-age  Online 
 total-lbas-read             n/a|n/a|  0    n/a    190891      Old-age  Online 


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdf1
  native-path:                 /sys/devices/pci0000:00/0000:00:01.0/0000:02:00.0/ata10/host9/target9:0:0/9:0:0:0/block/sdf/sdf1
  device:                      8:81
  device-file:                 /dev/sdf1
    presentation:              /dev/sdf1
    by-id:                     /dev/disk/by-id/ata-OCZ-AGILITY3_OCZ-3AV443TY6S6AUMO0-part1
    by-id:                     /dev/disk/by-id/wwn-0x5e83a97ee0aa19e8-part1
    by-id:                     /dev/disk/by-uuid/7e0a82d3-15f5-4a42-9393-3c010106ff42
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  1
  mount paths:             /
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  automount hint:              
  size:                        107150835712
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ext4
  version:                     1.0
  uuid:                        7e0a82d3-15f5-4a42-9393-3c010106ff42
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sdf
    scheme:                    mbr
    number:                    1
    type:                      0x83
    flags:                     boot
    offset:                    1048576
    alignment offset:          0
    size:                      107150835712
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdf2
  native-path:                 /sys/devices/pci0000:00/0000:00:01.0/0000:02:00.0/ata10/host9/target9:0:0/9:0:0:0/block/sdf/sdf2
  device:                      8:82
  device-file:                 /dev/sdf2
    presentation:              /dev/sdf2
    by-id:                     /dev/disk/by-id/ata-OCZ-AGILITY3_OCZ-3AV443TY6S6AUMO0-part2
    by-id:                     /dev/disk/by-id/wwn-0x5e83a97ee0aa19e8-part2
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        1024
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sdf
    scheme:                    mbr
    number:                    2
    type:                      0x05
    flags:                    
    offset:                    107152931840
    alignment offset:          0
    size:                      12880708608
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sdf5
  native-path:                 /sys/devices/pci0000:00/0000:00:01.0/0000:02:00.0/ata10/host9/target9:0:0/9:0:0:0/block/sdf/sdf5
  device:                      8:85
  device-file:                 /dev/sdf5
    presentation:              /dev/sdf5
    by-id:                     /dev/disk/by-id/ata-OCZ-AGILITY3_OCZ-3AV443TY6S6AUMO0-part5
    by-id:                     /dev/disk/by-id/wwn-0x5e83a97ee0aa19e8-part5
    by-id:                     /dev/disk/by-uuid/df8c66ce-6263-4f26-9055-730dca680132
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        12880707584
  block size:                  512
  job underway:                no
  usage:                       other
  type:                        swap
  version:                     2
  uuid:                        df8c66ce-6263-4f26-9055-730dca680132
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sdf
    scheme:                    mbr
    number:                    5
    type:                      0x82
    flags:                    
    offset:                    107152932864
    alignment offset:          0
    size:                      12880707584
    label:                     
    uuid:                      


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sr0
  native-path:                 /sys/devices/pci0000:00/0000:00:01.0/0000:02:00.1/ata1/host0/target0:0:1/0:0:1:0/block/sr0
  device:                      11:0
  device-file:                 /dev/sr0
    presentation:              /dev/sr0
    by-id:                     /dev/disk/by-id/ata-_NEC_DVD_RW_ND-3530A
  detected at:                 2015-04-30T13:34:37 CEST
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
  automount hint:              
  size:                        0
  block size:                  0
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  drive:
    vendor:                    _NEC
    model:                     _NEC DVD_RW ND-3530A
    revision:                  1.80
    serial:                    
    WWN:                       
    detachable:                0
    can spindown:              0
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 1
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     
      compat:                  optical_cd optical_cd_r optical_cd_rw optical_dvd optical_dvd_plus_r optical_dvd_plus_r_dl optical_dvd_plus_rw optical_dvd_r optical_dvd_rw optical_mrw optical_mrw_w
    interface:                 scsi
    if speed:                  (unknown)
    ATA SMART:                 not available


========================================================================
Showing information for /org/freedesktop/UDisks/devices/sr1
  native-path:                 /sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host16/target16:0:0/16:0:0:1/block/sr1
  device:                      11:1
  device-file:                 /dev/sr1
    presentation:              /dev/sr1
    by-id:                     /dev/disk/by-id/usb-SanDisk_Cruzer_077430189640FECF-0:1
    by-path:                   /dev/disk/by-path/pci-0000:00:1a.7-usb-0:1:1.0-scsi-0:0:0:1
  detected at:                 2015-04-30T13:34:37 CEST
  system internal:             0
  removable:                   1
  has media:                   1 (detected at 2015-04-30T13:34:37 CEST)
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
  automount hint:              
  size:                        100661248
  block size:                  2048
  job underway:                no
  usage:                       filesystem
  type:                        iso9660
  version:                     Joliet Extension
  uuid:                        
  label:                       U3 System
  optical disc:
    blank:                     0
    appendable:                0
    closed:                    0
    num tracks:                1
    num audio tracks:          0
    num sessions:              1
  drive:
    vendor:                    SanDisk
    model:                     Cruzer
    revision:                  8.01
    serial:                    077430189640FECF
    WWN:                       
    detachable:                1
    can spindown:              0
    rotational media:          Yes, unknown rate
    write-cache:               unknown
    ejectable:                 1
    adapter:                   Unknown
    ports:
    similar devices:
    media:                     optical_cd
      compat:                  optical_cd optical_mrw optical_mrw_w
    interface:                 usb
    if speed:                  480000000 bits/s
    ATA SMART:                 not available


========================================================================


[HR][/HR]sudo dmsetup ls:


isw_dafhbfdidg_Volume0p1    (252:1)
isw_dafhbfdidg_Volume0    (252:0)

[HR][/HR]cat /etc/fstab



proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=7e0a82d3-15f5-4a42-9393-3c010106ff42 /               ext4    errors=remount-ro 0       1
UUID=df8c66ce-6263-4f26-9055-730dca680132 none            swap    sw              0       0

[HR][/HR]df


Filesystem                            1K-blocks       Used Available Use% Mounted on
/dev/sdf1                             102865192   71901136  25715700  74% /
none                                          4          0         4   0% /sys/fs/cgroup
udev                                    6140680          4   6140676   1% /dev
tmpfs                                   1230312       1796   1228516   1% /run
none                                       5120          0      5120   0% /run/lock
none                                    6151544      33528   6118016   1% /run/shm
none                                     102400         60    102340   1% /run/user
/dev/sdc1                               7839740    5772900   2066840  74% /media/jonathan/1C24055724053574
/dev/mapper/isw_dafhbfdidg_Volume0p1 1953494012 1314043692 639450320  68% /media/Disk1

---

