---
title: "burner not working"
date: 2009-03-15
forum: Hardware
---

### Post by reformy on 2009-03-15
hi all
i have a new DVD burner i installed in my mythbuntu machine (8.10):
```
  *-cdrom:0
       description: DVD-RAM writer
       product: DVD-RAM GH22NP20
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
```
The drive won't work. It is connected and running (spinning) but if i try burning with GnomeBaker i get (for CD or DVD):
```
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
```
If I put the Ububntu install CD i can see it, but the file explorer keeps crashing while browsing the CD.

any ideas?

---

