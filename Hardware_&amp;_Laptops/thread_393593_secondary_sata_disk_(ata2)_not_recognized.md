---
title: "secondary sata disk (ata2) not recognized"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by misterplow on 2007-03-25
Hey there everyone -- I normally consider myself to be a moderately advanced linux admin, but something has me totally stumped.

I have a DELL PowerEdge SC430 which has 4 SATA ports on the motherboard. One of those ports is used by the harddisk that came with the machine.

Ubuntu 6.10 (Edge) recognized this onboard SATA disk and installed just fine. My problem is that I can't get a second SATA disk (that I subsequently installed) to be recognized. I've tried swapping cables and SATA ports on the motherboard, but the results do not change.

This is with a new SATA cable that I attached myself.

Here is what I thought was relevant output from dmesg:

root@kuro:~# dmesg |grep -i ata
[17179569.184000]  BIOS-e820: 000000000fe8ec00 - 000000000fe90c00 (ACPI data)
[17179569.184000] Memory: 248424k/260656k available (1910k kernel code, 11572k reserved, 1070k data, 308k init, 0k highmem)
[17179573.900000] hda: GCR-8485B, ATAPI CD/DVD-ROM drive
[17179574.588000] hda: ATAPI 48X CD-ROM drive, 128kB Cache, UDMA(33)
[17179574.640000] libata version 1.20 loaded.
[17179574.644000] ata_piix 0000:00:1f.2: version 1.05
[17179574.644000] ata1: SATA max UDMA/133 cmd 0xFE00 ctl 0xFE12 bmdma 0xFEA0 irq 225
[17179574.644000] ata2: SATA max UDMA/133 cmd 0xFE20 ctl 0xFE32 bmdma 0xFEA8 irq 225
[17179574.816000] ata1: dev 0 cfg 49:2f00 82:746b 83:7f01 84:4023 85:7469 86:3e01 87:4023 88:207f
[17179574.816000] ata1: dev 0 ATA-7, max UDMA/133, 156250000 sectors: LBA48
[17179574.828000] ata1: dev 0 configured for UDMA/133
[17179574.828000] scsi0 : ata_piix
[17179574.984000] ata2: disabling port
[17179574.984000] scsi1 : ata_piix
[17179574.988000]   Vendor: ATA       Model: WDC WD800JD-75MS  Rev: 10.0
[17179576.284000] EXT3-fs: mounted filesystem with ordered data mode.
[17179596.700000] ReiserFS: sdc1: using ordered data mode
[17179596.864000] EXT3-fs: mounted filesystem with ordered data mode.
[17179596.920000] EXT3-fs: mounted filesystem with ordered data mode.
[17179596.976000] EXT3-fs: mounted filesystem with ordered data mode.
[17179597.056000] EXT3-fs: mounted filesystem with ordered data mode.



The "ata2: disabling port" line seems to indicate the problem, but it is a little bit odd because several lines above that the 2nd SATA port seems to be recognized.


I feel like I've just been stabbing in the dark, but what I've tried so far is:
[LIST]
[*]using modconf to load several of the sata_XX modules
[*]pass grub the "libata.atapi_enabled=1" option
[/LIST]

Rather than doing something exotic and possbly breaknig something, I would like to ask the forum whether there is something relatively simple that I am overlooking.

Oh - I have not yet mucked around in the BIOS. My initial feeling was that since the "[17179574.644000] ata2: SATA max . . . " line appeared in the output of dmesg that the BIOS was at least seeing something (and could be left alone).

Thank you for any input or ideas you have.

---

### Post by misterplow on 2007-04-02
Sorry to respond to my own post.

As it turns out, the BIOS setting for any SATA drive other than 0 was set to "off". So . . changing the BIOS setting to "on" fixed my problem.

It's a little embarrassing that this was the solution, but I'll post this here for anyone else who might benefit from hearing this.

---

