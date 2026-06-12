---
title: "Problem with Serial ATA"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by Scofield on 2006-07-25
I've recently bought a CSATACOMBO card. The card itself is recognized by ubuntu, but the sata disk connected to it isn't.

This is the information given by the lspci command:
```
0000:00:0b.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
```

and this is the information given by the lshw command:
```
*-storage:0
   description: RAID bus controller
   product: VT6421 IDE RAID Controller
   vendor: VIA Technologies, Inc.
   physical id: b
   bus info: pci@00:0b.0
   logical name: scsi0
   logical name: scsi1
   version: 50
   width: 32 bits
   clock: 33MHz
   capabilities: storage bus_master cap_list scsi-host
   configuration: driver=sata_via
   resources: ioport:d800-d80f ioport:d400-d40f ioport:d000-d00f ioport:b800-b80f ioport:b400-b41f ioport:b000-b0ff irq:169
```

Hope anybody can help me. Thanks in advance.

---

