---
title: "system freeze whith empty DVD"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by boerne on 2007-04-28
Hi there,
I have some problems with my dvd-drive. When inserting an empty DVD the system freezes for approximately 5 minutes without mounting the DVD. This does not occur neither with empty CDs nor with DVDs with data.

thanks.

here is my /var/log/messages
```

Apr 28 12:53:05 sx20 kernel: [19160.496000]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
Apr 28 12:53:05 sx20 kernel: [19167.764000] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Apr 28 12:53:05 sx20 kernel: [19167.764000] ata1: failed to recover some devices, retrying in 5 secs
Apr 28 12:53:05 sx20 kernel: [19172.768000] ata1: soft resetting port
Apr 28 12:53:05 sx20 kernel: [19173.488000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19173.488000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19173.488000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19173.488000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19173.544000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19173.544000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19173.544000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19173.544000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19173.588000] ata1.00: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19173.756000] ata1.01: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19173.756000] ata1: EH complete
Apr 28 12:53:05 sx20 kernel: [19173.756000] SCSI device sda: 155556817 512-byte hdwr sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19173.756000] sda: Write Protect is off
Apr 28 12:53:05 sx20 kernel: [19180.916000]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
Apr 28 12:53:05 sx20 kernel: [19188.200000] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Apr 28 12:53:05 sx20 kernel: [19188.200000] ata1: failed to recover some devices, retrying in 5 secs
Apr 28 12:53:05 sx20 kernel: [19193.204000] ata1: soft resetting port
Apr 28 12:53:05 sx20 kernel: [19193.924000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19193.924000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19193.924000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19193.924000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19193.980000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19193.980000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19193.980000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19193.980000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19194.024000] ata1.00: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19194.188000] ata1.01: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19194.188000] ata1: EH complete
Apr 28 12:53:05 sx20 kernel: [19194.188000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 12:53:05 sx20 kernel: [19201.340000]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
Apr 28 12:53:05 sx20 kernel: [19208.608000] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Apr 28 12:53:05 sx20 kernel: [19208.608000] ata1: failed to recover some devices, retrying in 5 secs
Apr 28 12:53:05 sx20 kernel: [19213.612000] ata1: soft resetting port
Apr 28 12:53:05 sx20 kernel: [19214.332000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19214.332000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19214.332000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19214.332000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19214.392000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19214.392000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19214.392000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19214.392000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19214.440000] ata1.00: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19214.604000] ata1.01: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19214.604000] ata1: EH complete
Apr 28 12:53:05 sx20 kernel: [19214.604000] SCSI device sda: 155556817 512-byte hdwr sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19214.604000] sda: Write Protect is off
Apr 28 12:53:05 sx20 kernel: [19221.760000]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
Apr 28 12:53:05 sx20 kernel: [19229.028000] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Apr 28 12:53:05 sx20 kernel: [19229.028000] ata1: failed to recover some devices, retrying in 5 secs
Apr 28 12:53:05 sx20 kernel: [19234.032000] ata1: soft resetting port
Apr 28 12:53:05 sx20 kernel: [19234.752000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19234.752000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19234.752000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19234.752000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19234.804000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19234.804000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19234.804000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19234.804000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19234.852000] ata1.00: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19235.016000] ata1.01: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19235.016000] sr 0:0:1:0: SCSI error: return code = 0x08000002
Apr 28 12:53:05 sx20 kernel: [19235.016000] sr0: Current [descriptor]: sense key: Medium Error
Apr 28 12:53:05 sx20 kernel: [19235.016000]     Additional sense: Address mark not found for data field
Apr 28 12:53:05 sx20 kernel: [19235.016000] Descriptor sense data with sense descriptors (in hex):
Apr 28 12:53:05 sx20 kernel: [19235.016000]         72 03 13 00 00 00 00 0e 09 0c 00 51 00 03 00 00 
Apr 28 12:53:05 sx20 kernel: [19235.016000]         00 00 00 00 b0 51 
Apr 28 12:53:05 sx20 kernel: [19235.016000] end_request: I/O error, dev sr0, sector 0
Apr 28 12:53:05 sx20 kernel: [19235.016000] ata1: EH complete
Apr 28 12:53:05 sx20 kernel: [19235.016000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 12:53:05 sx20 kernel: [19242.180000]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
Apr 28 12:53:05 sx20 kernel: [19249.448000] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Apr 28 12:53:05 sx20 kernel: [19249.448000] ata1: failed to recover some devices, retrying in 5 secs
Apr 28 12:53:05 sx20 kernel: [19254.452000] ata1: soft resetting port
Apr 28 12:53:05 sx20 kernel: [19255.172000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19255.172000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19255.172000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19255.172000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19255.228000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19255.228000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19255.228000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19255.228000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19255.276000] ata1.00: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19255.440000] ata1.01: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19255.440000] ata1: EH complete
Apr 28 12:53:05 sx20 kernel: [19255.440000] SCSI device sda: 155556817 512-byte hdwr sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19255.440000] sda: Write Protect is off
Apr 28 12:53:05 sx20 kernel: [19262.600000]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
Apr 28 12:53:05 sx20 kernel: [19269.868000] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Apr 28 12:53:05 sx20 kernel: [19269.868000] ata1: failed to recover some devices, retrying in 5 secs
Apr 28 12:53:05 sx20 kernel: [19274.872000] ata1: soft resetting port
Apr 28 12:53:05 sx20 kernel: [19275.536000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19275.536000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19275.536000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19275.536000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19275.596000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19275.596000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19275.596000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19275.596000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19275.644000] ata1.00: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19275.808000] ata1.01: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19275.808000] ata1: EH complete
Apr 28 12:53:05 sx20 kernel: [19275.808000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 12:53:05 sx20 kernel: [19282.924000]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
Apr 28 12:53:05 sx20 kernel: [19290.192000] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Apr 28 12:53:05 sx20 kernel: [19290.192000] ata1: failed to recover some devices, retrying in 5 secs
Apr 28 12:53:05 sx20 kernel: [19295.196000] ata1: soft resetting port
Apr 28 12:53:05 sx20 kernel: [19295.916000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19295.916000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19295.916000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19295.916000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19295.976000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19295.976000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19295.976000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19295.976000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19296.024000] ata1.00: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19296.188000] ata1.01: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19296.188000] ata1: EH complete
Apr 28 12:53:05 sx20 kernel: [19296.188000] SCSI device sda: 155556817 512-byte hdwr sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19303.344000]          res 51/51:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
Apr 28 12:53:05 sx20 kernel: [19310.612000] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Apr 28 12:53:05 sx20 kernel: [19310.612000] ata1: failed to recover some devices, retrying in 5 secs
Apr 28 12:53:05 sx20 kernel: [19315.616000] ata1: soft resetting port
Apr 28 12:53:05 sx20 kernel: [19316.280000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19316.280000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19316.280000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19316.280000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19316.336000] ata1.00: ata_hpa_resize 1: sectors = 155556817, hpa_sectors = 156368016
Apr 28 12:53:05 sx20 kernel: [19316.336000] ata1.00: Host Protected Area detected.
Apr 28 12:53:05 sx20 kernel: [19316.336000]      current size : 155556817 sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19316.336000]      native  size : 156368016 sectors (80060 MB)
Apr 28 12:53:05 sx20 kernel: [19316.384000] ata1.00: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19316.548000] ata1.01: configured for UDMA/33
Apr 28 12:53:05 sx20 kernel: [19316.548000] sr 0:0:1:0: SCSI error: return code = 0x08000002
Apr 28 12:53:05 sx20 kernel: [19316.548000] sr0: Current [descriptor]: sense key: Medium Error
Apr 28 12:53:05 sx20 kernel: [19316.548000]     Additional sense: Address mark not found for data field
Apr 28 12:53:05 sx20 kernel: [19316.548000] Descriptor sense data with sense descriptors (in hex):
Apr 28 12:53:05 sx20 kernel: [19316.548000]         72 03 13 00 00 00 00 0e 09 0c 00 51 00 03 00 00 
Apr 28 12:53:05 sx20 kernel: [19316.548000]         00 00 00 00 b0 51 
Apr 28 12:53:05 sx20 kernel: [19316.548000] end_request: I/O error, dev sr0, sector 0
Apr 28 12:53:05 sx20 kernel: [19316.548000] ata1: EH complete
Apr 28 12:53:05 sx20 kernel: [19316.548000] sda: Write Protect is off
Apr 28 12:53:05 sx20 kernel: [19316.548000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 12:53:05 sx20 kernel: [19316.568000] SCSI device sda: 155556817 512-byte hdwr sectors (79645 MB)
Apr 28 12:53:05 sx20 kernel: [19316.568000] sda: Write Protect is off
Apr 28 12:53:05 sx20 kernel: [19316.568000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

 hdparm -i /dev/scd0 
```

/dev/scd0:

 Model=TSSTcorpCD/DVDW TS-L632B                , FwRev=TM31    , SerialNo=85WU700079          
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 1:  ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode


```


fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7064d16e-642d-48b7-934f-70a3c7fda5df /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=cd586168-db55-4ba9-a0a3-f214795fe154 /home           ext3    defaults        0       2
# /dev/sda5
UUID=f09829f1-487c-4da4-869a-63ceb68f0f84 /media/daten    ext3    defaults        0       2
# /dev/sda6
UUID=1a80f8c3-60c9-44d1-a0f4-d69cac8d670f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

