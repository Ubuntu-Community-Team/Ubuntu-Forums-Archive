---
title: "cd burning fails on thinkpad t61p"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by arsenix on 2007-10-29
I have gutsy running relatively well on my T61p now, but one remaining issue is that I don't seem to be able to burn cd's.  This frankly surprised me since I haven't had issues with cd burning under linux in many years.

cdrecord finds the drive:
**cdrecord -scanbus**
```
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
Linux sg driver version: 3.5.34
Using libscg version 'schily-0.9'.
scsibus0:
        0,0,0     0) 'HL-DT-ST' 'DVDRAM GSA-U10N ' '1.05' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
scsibus2:
        2,0,0   200) 'ATA     ' 'Hitachi HTS72202' 'DC4O' Disk
        2,1,0   201) *
        2,2,0   202) *
        2,3,0   203) *
        2,4,0   204) *
        2,5,0   205) *
        2,6,0   206) *
        2,7,0   207) *
```

**cdrecord -inq**
```
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
Linux sg driver version: 3.5.34
Using libscg version 'schily-0.9'.
No target specified, trying to find one...
Using dev=0,0,0.
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-U10N '
Revision       : '1.05'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
```

When I do a burn, cdrecord says:
```
Last chance to quit, starting real write    0 seconds. Operation starts.
cdrecord: WARNING: Drive returns wrong startsec (0) using -150
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 10 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 2A 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 200s
write track pad data: error after 0 bytes
BFree: 1029 K BSize: 1029 K
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 10 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 2A 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 200s
write track data: error after 0 bytes
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.
```

and the disc is no longer empty, but not valid (made many coasters so far).  I tried -tao mode, as well as trying to burn at lower speeds with no change.  During the burn, the dmesg fills up with quite a few messages like this:
```
[ 4289.524000] end_request: I/O error, dev sr0, sector 0
[ 4289.524000] Buffer I/O error on device sr0, logical block 0
```

Am I missing anything here?

This is the relevant section from dmesg where the drive is initialized, which looks fine:
```
[    3.948000] scsi0 : ata_piix
[    3.948000] scsi1 : ata_piix
[    3.948000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011830 irq 14
[    3.948000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011838 irq 15
[    4.004000] usb 1-2: USB disconnect, address 2
[    4.268000] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-U10N, 1.05, max UDMA/33
[    4.440000] ata1.00: configured for UDMA/33
[    4.440000] ata2: port disabled. ignoring.
[    4.440000] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-U10N  1.05 PQ: 0 ANSI: 5
[    4.440000] ahci 0000:00:1f.2: version 2.2
[    4.440000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
[    4.440000] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match
[    4.460000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.460000] Uniform CD-ROM driver Revision: 3.20
[    4.460000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.460000] sr 0:0:0:0: Attached scsi generic sg0 type 5
```

Any ideas?

James

---

### Post by MeanderingCode on 2007-11-03
I just have to say that this is my worst linux experience yet (installing Gutsy)  Dapper:great; Fesity: great; Debian, Knoppix, Slax, Backtrack: great.  All of a sudden, shitty.

This is one of my problems, also.  Read DVD's fine for a while, now i can't rip them, nor burn cds.

Insert dvd into drive after a dmesg -c, after mounted, here's the dmesg:
```
[14487.552000] end_request: I/O error, dev sr0, sector 1248
[14487.652000] UDF-fs: Partition marked readonly; forcing readonly mount
[14487.720000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'E2938', timestamp 2007/01/22 04:01 (1e5c)

```

Cleared dmesg, tried copying to iso w/ dd, here's output:
```
root@host:/# dd if=/dev/sr0 of=/media/disk-1/video/backup.iso
dd: reading `/dev/sr0': Input/output error
1080+0 records in
1080+0 records out
552960 bytes (553 kB) copied, 3.33209 seconds, 166 kB/s

```
```
root@host:/# dmesg
[14885.380000] end_request: I/O error, dev sr0, sector 1080
[14885.380000] printk: 72 messages suppressed.
[14885.380000] Buffer I/O error on device sr0, logical block 270
[14885.380000] Buffer I/O error on device sr0, logical block 271
[14885.380000] Buffer I/O error on device sr0, logical block 272
[14885.380000] Buffer I/O error on device sr0, logical block 273
[14885.380000] Buffer I/O error on device sr0, logical block 274
[14885.380000] Buffer I/O error on device sr0, logical block 275
[14885.380000] Buffer I/O error on device sr0, logical block 276
[14885.380000] Buffer I/O error on device sr0, logical block 277
[14885.380000] Buffer I/O error on device sr0, logical block 278
[14885.380000] Buffer I/O error on device sr0, logical block 279
[14885.400000] end_request: I/O error, dev sr0, sector 1256

```

Just bumping and confirming.  Haven't run diagnostics on burning, may be a Brasero problem (freezes while "getting size").

---

