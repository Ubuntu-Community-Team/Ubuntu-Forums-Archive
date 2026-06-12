---
title: "How can I optimize my hard disk?"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by aaronfromchina on 2006-03-05
My hard disk is Barracuda 7200.7 SATA - ST3200822AS (200GB),
[http://www.seagate.com/cda/products/discsales/marketing/detail/0,1081,599,00.html](http://www.seagate.com/cda/products/discsales/marketing/detail/0,1081,599,00.html) 

hdparm -I /dev/sda outputs the following:
/dev/sda:

ATA device, with non-removable media
Model Number: ST3200822AS
Serial Number: 4LJ34NQA
Firmware Revision: 3.01
Standards:
Used: ATA/ATAPI-6 T13 1410D revision 2
Supported: 6 5 4 3
Configuration:
Logical max current
cylinders 16383 16383
heads 16 16
sectors/track 63 63
-- 
CHS current addressable sectors: 16514064
LBA user addressable sectors: 268435455
LBA48 user addressable sectors: 390721968
device size with M = 1024*1024: 190782 MBytes
device size with M = 1000*1000: 200049 MBytes (200 GB)
Capabilities:
LBA, IORDY(can be disabled)
bytes avail on r/w long: 4 Queue depth: 1
Standby timer values: spec'd by Standard, no device specific minimum
R/W multiple sector transfer: Max = 16 Current = 16
Recommended acoustic management value: 254, current value: 0
DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
Cycle time: min=120ns recommended=120ns
PIO: pio0 pio1 pio2 pio3 pio4
Cycle time: no flow control=240ns IORDY flow control=120ns
Commands/features:
Enabled Supported:
* READ BUFFER cmd
* WRITE BUFFER cmd
* Host Protected Area feature set
* Look-ahead
* Write cache
* Power Management feature set
Security Mode feature set
* SMART feature set
* FLUSH CACHE EXT command
* Mandatory FLUSH CACHE command
* Device Configuration Overlay feature set
* 48-bit Address feature set
SET MAX security extension
* DOWNLOAD MICROCODE cmd
* SMART self-test
* SMART error logging
Security:
Master password revision code = 65534
supported
not enabled
not locked
not frozen
not expired: security count
not supported: enhanced erase
Checksum: correct 

hdparm /dev/sda outputs the following:
/dev/sda:
IO_support = 0 (default 16-bit)
readonly = 0 (off)
readahead = 256 (on)
geometry = 24321/255/63, sectors = 390721968, start = 0 

What can I do next? What the IO_support does the SATA support?

Thank you.

---

### Post by aslocum on 2006-03-05
hdparm does not support SATA drives.
and you are already using udma6 and DMA is always on with SATA drives

---

