---
title: "SATA ports no longer working after upgrade from 17.10 to 18.04.1 / 18.10"
date: 2019-01-31
forum: Hardware
---

### Post by valentijn1977 on 2019-01-31
Hi,




After upgrading from 17.10 to 18.04.1 2 of my 6 SATA ports no longer work.




It's an older system with H55 chipset.




System boots fine, but as soon as I try to do something with the disks on these 2 ports, the system becomes extremely slow and eventually freezes.




I am seeing these errors in dmesg/syslog:




```

Jan 30 18:09:20 NAS kernel: [  256.611306] ata1: lost interrupt (Status 0x0)
Jan 30 18:09:20 NAS kernel: [  256.611332] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0 frozen
Jan 30 18:09:20 NAS kernel: [  256.611374] ata1.01: failed command: READ DMA
Jan 30 18:09:20 NAS kernel: [  256.611400] ata1.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 dma 4096 in
Jan 30 18:09:20 NAS kernel: [  256.611400]          res 40/00:00:00:00:00/00:00:00:00:00/50 Emask 0x4 (timeout)
Jan 30 18:09:20 NAS kernel: [  256.611460] ata1.01: status: { DRDY }
Jan 30 18:09:20 NAS kernel: [  256.611487] ata1.00: hard resetting link
Jan 30 18:09:21 NAS kernel: [  256.927086] ata1.01: hard resetting link
Jan 30 18:09:21 NAS kernel: [  257.402833] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 30 18:09:21 NAS kernel: [  257.402854] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 30 18:09:21 NAS kernel: [  257.414933] ata1.00: configured for UDMA/133
Jan 30 18:09:21 NAS kernel: [  257.418940] ata1.01: configured for UDMA/133
Jan 30 18:09:21 NAS kernel: [  257.418940] ata1: EH complete

```




Happens with all cables and all disks I have. At first I thought it might be ACPI, but when booting with ACPI=off the problem persists.




When I revert back to kernel 4.13, the problem and errors dissappear.




It's disk /dev/sdb in the pasted output from ubuntu-bug: [https://pastebin.com/M3BjPwrS](https://pastebin.com/M3BjPwrS)




```

/org/freedesktop/UDisks2/block_devices/sdb:
   org.freedesktop.UDisks2.Block:
     Configuration:              []
     CryptoBackingDevice:        '/'
     Device:                     /dev/sdb
     DeviceNumber:               2064
     Drive:                      '/org/freedesktop/UDisks2/drives/WDC_WD15EARS_00Z5B1_WD_WMAVU2785748'
     HintAuto:                   false
     HintIconName:               
     HintIgnore:                 false
     HintName:                   
     HintPartitionable:          true
     HintSymbolicIconName:       
     HintSystem:                 true
     Id:                         by-id-ata-WDC_WD15EARS-00Z5B1_WD-WMAVU2785748
     IdLabel:                    
     IdType:                     
     IdUUID:                     
     IdUsage:                    
     IdVersion:                  
     MDRaid:                     '/'
     MDRaidMember:               '/'
     PreferredDevice:            /dev/sdb
     ReadOnly:                   false
     Size:                       1500301910016
     Symlinks:                   /dev/disk/by-id/ata-WDC_WD15EARS-00Z5B1_WD-WMAVU2785748
                                 /dev/disk/by-id/wwn-0x50014ee6aab31a17
                                 /dev/disk/by-path/pci-0000:00:1f.2-ata-1
     UserspaceMountOptions:      
   org.freedesktop.UDisks2.PartitionTable:
     Partitions:         ['/org/freedesktop/UDisks2/block_devices/sdb1']
     Type:               gpt
 
 /org/freedesktop/UDisks2/block_devices/sdb1:
   org.freedesktop.UDisks2.Block:
     Configuration:              []
     CryptoBackingDevice:        '/'
     Device:                     /dev/sdb1
     DeviceNumber:               2065
     Drive:                      '/org/freedesktop/UDisks2/drives/WDC_WD15EARS_00Z5B1_WD_WMAVU2785748'
     HintAuto:                   false
     HintIconName:               
     HintIgnore:                 false
     HintName:                   
     HintPartitionable:          true
     HintSymbolicIconName:       
     HintSystem:                 true
     Id:                         by-id-ata-WDC_WD15EARS-00Z5B1_WD-WMAVU2785748-part1
     IdLabel:                    
     IdType:                     ext4
     IdUUID:                     d5044565-01dc-4477-a0f4-416a813d030f
     IdUsage:                    filesystem
     IdVersion:                  1.0
     MDRaid:                     '/'
     MDRaidMember:               '/'
     PreferredDevice:            /dev/sdb1
     ReadOnly:                   false
     Size:                       1500300844544
     Symlinks:                   /dev/disk/by-id/ata-WDC_WD15EARS-00Z5B1_WD-WMAVU2785748-part1
                                 /dev/disk/by-id/wwn-0x50014ee6aab31a17-part1
                                 /dev/disk/by-partuuid/53c07570-73e1-4fa6-a577-e826c59d4b77
                                 /dev/disk/by-path/pci-0000:00:1f.2-ata-1-part1
                                 /dev/disk/by-uuid/d5044565-01dc-4477-a0f4-416a813d030f
     UserspaceMountOptions:      
   org.freedesktop.UDisks2.Filesystem:
     MountPoints:        
     Size:               1500300840960
   org.freedesktop.UDisks2.Partition:
     Flags:              0
     IsContained:        false
     IsContainer:        false
     Name:               
     Number:             1
     Offset:             1048576
     Size:               1500300844544
     Table:              '/org/freedesktop/UDisks2/block_devices/sdb'
     Type:               0fc63daf-8483-4772-8e79-3d69d8477de4
     UUID:               53c07570-73e1-4fa6-a577-e826c59d4b77

```




I am new to this, how can I debug/report this issue?




I've seen there were some power management improvements in kernel 4.15 (medium policy), but with ACPI off I think that's excluded as root cause?

I did another upgrade, this time to 18.10 but the problem persists.




Thank you,




Valentijn

---

### Post by valentijn1977 on 2019-02-10
Seems resolved in the latest kernel update installed yesterday:

[FONT=courier new]Linux NAS 4.18.0-15-generic #16-Ubuntu SMP Thu Feb 7 10:56:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux[/FONT]

---

