---
title: "Weird errors in dmesg during boot. Is this serious?"
date: 2010-06-06
forum: Hardware
---

### Post by dr_rimzi on 2010-06-06
Hello,

I just installed Ubuntu 10.04 on my freshly formatted disk.
I noticed that sometimes during boot it displays weird errors, 
so I looked it up in dmesg output:

```
[ 1775.637950] ata5.00: status: { DRDY ERR }
[ 1775.637953] ata5.00: error: { ICRC ABRT }
[ 1775.637965] ata5: hard resetting link
[ 1775.956079] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1775.972482] ata5.00: configured for UDMA/33
[ 1775.972500] ata5: EH complete
[ 1776.134510] ata5.00: exception Emask 0x12 SAct 0x0 SErr 0x1000500 action 0x6
[ 1776.134519] ata5.00: BMDMA stat 0x5
[ 1776.134524] ata5: SError: { UnrecovData Proto TrStaTrns }
[ 1776.134529] ata5.00: failed command: READ DMA
[ 1776.134537] ata5.00: cmd c8/00:00:0c:95:49/00:00:00:00:00/e6 tag 0 dma 131072 in
[ 1776.134539]          res 51/84:0c:00:00:00/84:0a:00:00:00/e0 Emask 0x12 (ATA bus error)

```

I have no idea what that means, or if it is some nasty problem :/
This is an old PC with new SATA HDD, just in case.

--

Thanks,
RimZi

---

### Post by matt-fender on 2010-06-06
You say new SATA hard drive old board, did you replace the cable? I would also run a SMART test on the drive just in case?

EDIT: Also check your BIOS for AHCI, if it supports it try enabling it and see if it makes any difference.

---

### Post by matt-fender on 2010-06-22
Have you had any more luck with this? I'm interested to know for future reference

---

### Post by Yellow Pasque on 2010-06-22
Check for BIOS updates too.

---

