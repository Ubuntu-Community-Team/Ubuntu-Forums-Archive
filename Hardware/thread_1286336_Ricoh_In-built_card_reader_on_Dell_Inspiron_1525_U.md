---
title: "Ricoh In-built card reader on Dell Inspiron 1525 Ubuntu 9.04"
date: 2009-10-08
forum: Hardware
---

### Post by shajul on 2009-10-08
I installed Ubuntu 9.04 about a month back and I was so happy that I removed the licenced factory installed Vista (which i really hated).

But now i realize that my card reader does not read MMC cards (SD i have not tried)..

This is the lspci | grep Ricoh 

02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:09.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


I tried..

[LIST]
[*]**setpci -s ‘02:09.0&#8242; 0xCA=0×57** (Write Enable)
[*]**setpci -s ‘02:09.0&#8242; 0xCB=0×02** (MMC Disable)
[*]**setpci -s ‘02:09.0&#8242; 0xCA=0×00** (Write Disable)
[/LIST]
but no effect..

I even modprobe -rv sdhci mmc_block mmc_core (after removing sdhci_pci), but it says mmc_core not found..
I again inserted sdhci and mmc_block..

I tried some more stuff, but no avail..

Pls help

---

### Post by shajul on 2009-10-10
Up...

---

### Post by IcarusR on 2009-10-10
A google search led me to this page [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208") which says it is a bug.

SD cards work but not MMC.

---

### Post by shajul on 2009-10-10
yes, a lot of bug reports have been filed..

but no solution i guess.. cant believe that ubuntu was stumped by a lowly card.

---

