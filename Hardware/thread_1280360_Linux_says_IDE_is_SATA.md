---
title: "Linux says IDE is SATA?"
date: 2009-10-01
forum: Hardware
---

### Post by AwesomeTux on 2009-10-01
Hello, I used the command dmesg and found this:

> [    0.541436] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[    0.541936] ata1: SATA max UDMA/133 cmd 0xe300 ctl 0xe400 bmdma 0xe700 irq 17
[    0.541942] ata2: SATA max UDMA/133 cmd 0xe500 ctl 0xe600 bmdma 0xe708 irq 17
[    0.846590] ata1: SATA link down (SStatus 0 SControl 300)
[    1.174588] ata2: SATA link down (SStatus 0 SControl 300)

So is the kernel thinking my IDE drive is a SATA? I know I have an IDE.

And the results of "sudo hdparm -tT /dev/sda" confirm my drive is IDE:

> /dev/sda:
 Timing cached reads:   962 MB in  2.00 seconds = 480.25 MB/sec
 Timing buffered disk reads:  166 MB in  3.03 seconds =  54.71 MB/sec

How can I check how Linux is set to use my drives?

---

### Post by Yellow Pasque on 2009-10-02
> [ 0.541436] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[ 0.541936] ata1: SATA max UDMA/133 cmd 0xe300 ctl 0xe400 bmdma 0xe700 irq 17
[ 0.541942] ata2: SATA max UDMA/133 cmd 0xe500 ctl 0xe600 bmdma 0xe708 irq 17
[ 0.846590] ata1: SATA link down (SStatus 0 SControl 300)
[ 1.174588] ata2: SATA link down (SStatus 0 SControl 300) 

This says nothing about your disk. It means you have a SATA controller on your motherboard with two connectors, and no devices are detected as being connected.

---

