---
title: "USB mp3 player: error I/O"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by giacomolg on 2007-07-31
Hello all,
my new mp3 player acts as a USB MSDC (reading from the manual...); I thought it should be well supported by the kernel, but for some reason I can mount it but when reading or writing from/to the device I get a I/O error...It works fine on Microsoft Windows, and I even re-formatted the disk (using a Windows tool) with FAT32, but the error is still there.

Some suspect log messages:

sdb: Write Protect is off
sdb: Mode Sense: 00 06 00 00
sdb: assuming drive cache: write through
sdb: **unknown partition table**

and then the actual error code:

sd 2:0:0:0: SCSI error: **return code = 0x70000**
end_request: I/O error, dev sdb, sector 18904 
(repeated over and over again)
[for more verbose log output see attachment]


**please help!!**

I have the error on both Dapper & Edgy

---

