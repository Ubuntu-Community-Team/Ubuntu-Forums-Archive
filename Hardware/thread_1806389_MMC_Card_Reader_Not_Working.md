---
title: "MMC Card Reader Not Working"
date: 2011-07-17
forum: Hardware
---

### Post by mnorgate on 2011-07-17
I have a Ricoh Co Ltd R5C822 card reader in my laptop running Ubuntu 11.04 but I cannot get it read MMC cards. I have looked around on the internet and found articles that say I need to disable the MMC reader so that it can use the SD one, dont quite understand, see below for output of lspci


lspci | grep Ricoh
08:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:03.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

