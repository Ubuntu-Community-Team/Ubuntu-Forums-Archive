---
title: "mdadm RAID not working - hardware problems..."
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by matc on 2008-01-24
Hi everybody,

I have problems getting my RAID system to run...

The hardware:

- One VIA VT6421A PCI RAID 0+1 controller card (without BIOS extensions)
- Another VIA VT6421A PCI RAID 0+1 controller card (with BIOS extensions) or as alternative a Silicon Image PCI RAID 0+1 controller card

all cards SATA 150 MBps and used in JBOD mode.

- four Samsung HJ501 500GB devices


in a 1,4 Ghz AMD Geode NX device with 1 GB RAM and a 120GB IDE root drive.


What happens? Either one of the disks (or it's partitions) do not get detected OR just loses connection when the software RAID5  (via mdadm) tries to initialize and reached more than 4% of the init phase. then the whole raid is unusable.

The first VT6421A card and 2 of the disks as standalone worked for 2 months without any problems..

Any ideas ???

---

### Post by Celeb on 2008-07-18
try changing your data cables, i got trouble in the past with RAID and SATA cables, but mine was at the instalation. :S 


If mdadm is not working for you, did you try to use dmraid?

I prefer mdadm ... but it is a solution ^^... good luck.


Joaquin Diaz Trepat

---

