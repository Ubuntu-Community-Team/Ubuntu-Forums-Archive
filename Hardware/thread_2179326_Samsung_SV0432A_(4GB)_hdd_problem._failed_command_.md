---
title: "Samsung SV0432A (4GB) hdd problem. failed command: FLUSH CACHE"
date: 2013-10-07
forum: Hardware
---

### Post by e-San on 2013-10-07
It's an old drive, but i need it at the moment.
It's quite slow, but stable system. Thats weird since there is P4@2600.
Here some informations:

```
root@localhost:~# hdparm -f /dev/sda

/dev/sda:

```
```

root@localhost:~# hdparm -F /dev/sda

/dev/sda:
 HDIO_DRIVE_CMD(flushcache) failed: Input/output error

```
```

root@localhost:~# hdparm -W0 /dev/sda

/dev/sda:
 setting drive write-caching to 0 (off)
 HDIO_DRIVE_CMD(flushcache) failed: Input/output error
 HDIO_DRIVE_CMD(flushcache) failed: Input/output error
 write-caching =  1 (on)

```
```

root@localhost:~# hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
    Model Number:       SAMSUNG SV0432A                         
    Serial Number:      0104J1FK928392
    Firmware Revision:  JV100-32
Standards:
    Used: ATA/ATAPI-4 X3T13 1153D revision 7 
    Supported: 4 3 2 
Configuration:
    Logical        max    current
    cylinders    8912    8912
    heads        15    15
    sectors/track    63    63
    --
    CHS current addressable sectors:    8421840
    LBA    user addressable sectors:    8421840
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:        4112 MBytes
    device size with M = 1000*1000:        4311 MBytes (4 GB)
    cache/buffer size  = 220 KBytes (type=DualPortCache)
Capabilities:
    LBA, IORDY(cannot be disabled)
    bytes avail on r/w long: 4
    Standby timer values: spec'd by Vendor
    R/W multiple sector transfer: Max = 16    Current = ?
    DMA: mdma0 mdma1 mdma2 udma0 *udma1 udma2 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
            SMART feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    DEVICE_RESET command
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd

```
```
root@localhost:~# dmesg |tail
[ 4928.102743] ata1: EH complete
[ 4928.110432] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 4928.110730] ata1.00: failed command: FLUSH CACHE
[ 4928.111766] ata1.00: cmd e7/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 4928.111766]          res 51/04:00:d7:a3:35/00:00:00:00:00/a0 Emask 0x1 (device error)
[ 4928.112143] ata1.00: status: { DRDY ERR }
[ 4928.112891] ata1.00: error: { ABRT }
[ 4928.130665] ata1.00: configured for PIO0
[ 4928.145900] ata1.01: configured for UDMA/33
[ 4928.146704] ata1: EH complete

```

as You can see, i tried to disable cache as suggested [http://forums.storagereview.com/index.php/topic/12261-ata-drives-and-flushing-write-cache/](http://forums.storagereview.com/index.php/topic/12261-ata-drives-and-flushing-write-cache/) but no chance.
Any way to work-around this problem?

Best regards!

---

