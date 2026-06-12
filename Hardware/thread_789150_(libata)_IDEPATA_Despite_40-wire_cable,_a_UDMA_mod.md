---
title: "(libata) IDE/PATA: Despite 40-wire cable, a UDMA mode to high is set"
date: 2008-05-10
forum: Hardware
---

### Post by Björn Schließmann on 2008-05-10
I have hardy on a computer with two IDE (PATA) ports. On the first, there is a udma66-capable harddisk as master and a udma66-capable DVD-ROM as slave. They are connected to the controller via a 40-wire cable; so only udma33 should be possible. But the DVD-ROM has a whole lot of reading errors, and dmesg shows at boot:

[   34.301317] ata1.00: ATA-4: WDC AC313000R, 17.01J17, max UDMA/66
[   34.301326] ata1.00: 25429824 sectors, multi 16: LBA
[   34.301355] ata1.01: ATAPI: Pioneer DVD-ROM ATAPIModel DVD-106S 0122, E1.22, max UDMA/66
[   34.301376] ata1.00: limited to UDMA/33 due to 40-wire cable
[   34.333313] ata1.00: configured for UDMA/33
[   34.505153] ata1.01: configured for UDMA/66

hdparm excerpt:

/dev/sda:
    DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4
/dev/scd0:
    DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4

I suspect the wrong mode is selected on the DVD drive. Am I misinterpreting; can anyone confirm this? I don't want to file a bug until I'm sure about the problem.

Also, how could I manually select the mode? With libata, hdparm doesn't work anymore, and Documentation/kernel-parameters.txt.gz only shows two libata parameters.

Regards,


Björn

---

