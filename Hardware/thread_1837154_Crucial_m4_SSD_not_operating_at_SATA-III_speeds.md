---
title: "Crucial m4 SSD not operating at SATA-III speeds"
date: 2011-09-01
forum: Hardware
---

### Post by MacUntu on 2011-09-01
I'm using a Crucial m4 SSD with an ASUS P8Z68-V motherboard and expected to get read rates above SATA-II speeds (~415MB/s actually), but I don't. They are stuck at ~283MB/s according to palimpsest.

hdparm suggests the drive is recognized as using the SATA-III interface I guess:

[http://paste.ubuntu.com/679645/](http://paste.ubuntu.com/679645/)

Any ideas how to fix this?

I'm using up-to-date Oneiric with kernel 3.0.0-9-generic.

Hm, dmesg output looks bad:

> [    2.534098] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.534463] ata1.00: ATA-9: M4-CT064M4SSD2, 0009, max UDMA/100
[    2.534465] ata1.00: 125045424 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.534882] ata1.00: configured for UDMA/100
[    2.535046] scsi 0:0:0:0: Direct-Access     ATA      M4-CT064M4SSD2   0009 PQ: 0 ANSI: 5


---

### Post by MacUntu on 2011-09-01
So, without my other HDD attached to a SATA-II port, the SSD seems to operate at full speed. Now to find out if that's a kernel or BIOS/controller issue. Oh dear!

---

### Post by MacUntu on 2011-09-02
I've been trying to reproduce the issue without luck, so I assume it was a connection problem. Very weird, but it's running at SATA-III speed now, seems to be a decent drive:

[IMG]http://img.xrmb2.net/images/285484.png[/IMG]

---

