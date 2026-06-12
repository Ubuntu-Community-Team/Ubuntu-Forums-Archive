---
title: "Hard Drives SATA versus IDE"
date: 2008-05-21
forum: Hardware
---

### Post by hal8000 on 2008-05-21
I have an UDMA100 IDE hard drive on an 80 wire cable. Due to a bug in the kernel the hard drive only runs at UDMA33 speeds.

At the moment I've returned to Feisty 7.04 and actually managed to boot with libATA emulation. Here's an extract from the boot messages and Feisty tells me both UDMA100 and UDMA133 drives are only running at 33Mbps


[    4.131768] ata1.00: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[    4.165703] ata1.01: ATA-7: WDC WD1600BB-55RDA0, 20.00K20, max UDMA/100
[    4.165712] ata1.00: limited to UDMA/33 due to 40-wire cable
[    4.165716] ata1.01: limited to UDMA/33 due to 40-wire cable
[    4.171592] ata1.00: configured for UDMA/33
[    4.187313] ata1.01: configured for UDMA/33
[    4.517583] ata2.01: ATAPI, max UDMA/33
[    4.690753] ata2.01: configured for UDMA/33


Testing with hdparm
root@orac:/home/anc# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   2038 MB in  2.00 seconds = 1019.56 MB/sec
 Timing buffered disk reads:   90 MB in  3.06 seconds =  29.41 MB/sec


The figures do indeed agree with kernel messages and Im missing performance.

This is really a question on performance, so hope someone with a native SATA can run

sudo hdparm -tT /dev/sda

and post results. If performance is much better I would expect faster boot times as well. Thanks in advance.

---

### Post by cprofitt on 2008-05-21
Just tagging your thread for the unanswered posts team.

---

### Post by ShangTsungOmega on 2008-05-21
Are you looking for SATA 1 or SATA 2 results?

---

### Post by hal8000 on 2008-05-22
> **ShangTsungOmega said:**
> Are you looking for SATA 1 or SATA 2 results?

I'd in interested in results for both. SATA2 Hard drives have dropped in price so if performance is better these would be a good investment.

---

### Post by hal8000 on 2008-05-23
I now have a single IDE drive and  a SATA. Having only one drive on the IDE cable has removed the problem of IRQ sharing, the native SATA drive is best:

 sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   1960 MB in  2.00 seconds = 980.30 MB/sec
 Timing buffered disk reads:  226 MB in  3.03 seconds =  74.68 MB/sec


my IDE drive (designated sda by libATA clocks in around 54MB/sec).

---

