---
title: "Slow hd and dvd drive, fail to set see DMA"
date: 2010-12-01
forum: Hardware
---

### Post by mauro.barrera on 2010-12-01
[I]My hard disk and CD/DVD IDE drives are slow.
I tried to check if DMA was enabled and got this for one of my hd[/I]

mo@darkstar:~$ sudo hdparm -d /dev/sda1

/dev/sda1:
 HDIO_GET_DMA failed: Inappropriate ioctl for device


*the same for DVD drive. *

mo@darkstar:~$ sudo hdparm -d /dev/sr0

/dev/sr0:
 HDIO_GET_DMA failed: Inappropriate ioctl for device

[I]I run ubuntu 10.10 on AMD 64 Athlon 3200+ (I had the same problems and never solved them with previous versions of ubuntu)

[I]I know Sheldon from BigBang Theory could help me on this, but I doubt he is monitoring this forum :). If anyone else can help her/his suggestions are welcomed. Thank you in advance:

Mauro[/I]

What follows is the output of some commands relevant to the description of my hw configuration and current status. [/I]

mo@darkstar:~$ dmesg | grep ATA
[    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
[    0.000000]   #2 [0001000000 - 0001a2ca64]    TEXT DATA BSS ==> [0001000000 - 0001a2ca64]
[    0.819384] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    0.819387] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.010477] ata1.00: ATA-5: MAXTOR 6L040J2, A93.0500, max UDMA/133
[    1.012073] ata1.01: ATA-7: Maxtor 6L300R0, BAH41G10, max UDMA/133
[    1.091885] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR 6L040J2   A93. PQ: 0 ANSI: 5
[    1.092361] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6L300R0   BAH4 PQ: 0 ANSI: 5
[    1.270332] ata2.00: ATAPI: PIONEER DVD-RW  DVR-112D, 1.21, max UDMA/66
[    1.270353] ata2.00: WARNING: ATAPI DMA disabled for reliability issues.  It can be enabled


mo@darkstar:~$ lspci | grep IDE
00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7)

---

