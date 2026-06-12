---
title: "Inconsistencies mounting and writing to external USB drive"
date: 2020-11-06
forum: Hardware
---

### Post by rmeas on 2020-11-06
I'm working on an NVIDIA AGX Xavier which is running 4.9.140-tegra, based on Ubuntu 18.04.

When I plug in an external USB drive (formatted as exFAT), it will sometimes be mounted in the user folder as `/media/USER/ssd1` and everything writes and reads correctly. Though, it will sometimes mount as `/media/5FA5-1920`. When it mounts in this way, writing will not work correctly. For example, attempting to rsync to that device will result in errors such as 

```
rsync: chgrp "/media/5FA5-1920/Log_dump" failed: Operation not permitted (1)
```

It will continue to "write" but at the end of the operation, only the directory structure is present, none of the files.

Here's the DMESG:
```

[ 1372.243918] usb 2-4: new SuperSpeed USB device number 13 using tegra-xusb
[ 1372.264692] usb 2-4: New USB device found, idVendor=0781, idProduct=558c
[ 1372.264704] usb 2-4: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 1372.264711] usb 2-4: Product: Extreme SSD
[ 1372.264718] usb 2-4: Manufacturer: SanDisk
[ 1372.264726] usb 2-4: SerialNumber: 323032375032343030383437
[ 1372.270680] scsi host2: uas
[ 1372.271769] scsi 2:0:0:0: Direct-Access     SanDisk  Extreme SSD      1012 PQ: 0 ANSI: 6
[ 1372.332938] sd 2:0:0:0: [sda] Spinning up disk...
[ 1372.333669] scsi 2:0:0:1: Enclosure         SanDisk  SES Device       1012 PQ: 0 ANSI: 6
[ 1373.359619] .
[ 1374.383620] .
[ 1374.383875] ready
[ 1374.384125] sd 2:0:0:0: [sda] 3907028992 512-byte logical blocks: (2.00 TB/1.82 TiB)
[ 1374.384303] sd 2:0:0:0: [sda] 4096-byte physical blocks
[ 1374.385118] sd 2:0:0:0: [sda] Write Protect is off
[ 1374.385226] sd 2:0:0:0: [sda] Mode Sense: 67 00 10 08
[ 1374.385516] sd 2:0:0:0: [sda] Write cache: disabled, read cache: enabled, supports DPO and FUA
[ 1374.412464]  sda: sda1
[ 1374.414739] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, supports DPO and FUA
[ 1374.415057] sd 2:0:0:0: [sda] Attached SCSI disk

```

---

