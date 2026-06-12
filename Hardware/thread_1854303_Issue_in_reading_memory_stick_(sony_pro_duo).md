---
title: "Issue in reading memory stick (sony pro duo)"
date: 2011-10-04
forum: Hardware
---

### Post by nolasco_fernando on 2011-10-04
hi all, i have a problem reading my memory stick "Sony Memory PRO Duo". Im using Ubuntu 10.10, running on an HP Pavillion. USB flash drives is automatically mounted, so theres no problem about it, but memory stick is an issue. i check /dev/ if there is a device added each time i insert the stick, hoping to mount it manually, but there are no added devices. 

i check pci buses using lspci 

(--output ommitted--)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

i think the result show it identified the pci bus and then i check the loaded module using lsmod

(--output omiited--)
firewire_ohci 21106 0
firewire_core 46643 1 firewire_ohci
(--output omitted--)

actually i'm not sure if ubuntu 10.10 loaded all the pci bus in my laptop based on this result.

i hope someone can help

thanks

---

### Post by diasf on 2011-10-04
The device won't be created when you plug the card. It's always there.

Plug it, it will automatically mount. type "mount" and check which file is the corresponding device.

---

