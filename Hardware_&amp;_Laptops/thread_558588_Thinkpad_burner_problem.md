---
title: "Thinkpad burner problem"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by Thas on 2007-09-24
Hi,

I have installed Ubuntu on my laptop (thinkpad t43) a few weeks ago and since then I'm experiencing some burning problems. I though this was hardware related and so I got my burner changed but I still have the problem and no idea of how to resolve it.

Here is an example of what happen : 

thas@thas-laptop:/media/sda5/Mes vidéos$ wodim test.avi
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
Quickly guessing the name of a drive capable to write CD-R, please wait...
Found /dev/cdrw, assuming dev=/dev/cdrw
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'MATSHITA'
Identification : 'DVD-RAM UJ-822Sy'
Revision       : 'RC01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO
Speed set to 1764 KB/s
Starting to write CD/DVD at speed  10.0 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 05 6D 30 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 03 00 05 6A CD 0A 00 13 00 00 10 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x10 Qual 0x00 (id crc or ecc error) Fru 0x0
Sense flags: Blk 355021 (valid) 
resid: 63488
cmd finished after 0.059s timeout 40s
write track data: error after 728334336 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 13 00 00 10 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x10 Qual 0x00 (id crc or ecc error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 22.176s timeout 480s
cmd finished after 22.176s timeout 480s
wodim: Cannot fixate disk.

Thanks

---

