---
title: "Edgy and PCI-X"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by jchung on 2007-03-21
I just installed Ubuntu 6.10 Server onto a new server and noticed something odd. First, here is the spec for the server:

- 2.4 Ghz Celeron
- Supermicro P4SCT motherboard
- 3Ware 9550SX-8LP
- 7 x 250GB WD disks (6 disk RAID 5 + 1 hot spare)
- 2 x 80GB WD disks (onboard SATA ports)


Now... the 3Ware card is a PCI-X card and supports 64bit / 66Mhz. 

The Supermicro motherboard has 3 PCI-X slots at 64bit / 66Mhz.

When I run a 'lshw', it shows that the 3Ware card is 64bit / 66Mhz but it shows the PCI-X slot as 32bit / 66Mhz. 

Also, when I perform sequential read/write tests, I can't seem to get above 200MB/s (for both reads and writes). I would normally expect reads to be faster than writes so this leads me to believe the bottleneck is not the disks and either is in the 3Ware card or the PCI-X bus. 

Anyone else see something similar? where the PCI-X slot should be 64bit but lshw reports it as being 32bit ? Or perhaps where the driver doesn't recognize the slot properly ?

---

