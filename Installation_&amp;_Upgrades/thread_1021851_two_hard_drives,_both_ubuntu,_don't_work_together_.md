---
title: "two hard drives, both ubuntu, don't work together well"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by ShirishAg75 on 2008-12-26
Hi all, 
 I have a 160 IDE GB and an 80 GB IDE HDD.  Both individually work great. But if I try to have both on them together it doesn't come good. 

This is excerpt from syslog. 

```

Dec 26 05:30:30 ubuntu kernel: [    4.924525] ata1.00: ATA-7: SAMSUNG SP0802N, TK100-24, max UDMA/100
Dec 26 05:30:30 ubuntu kernel: [    4.924594] ata1.00: 156368016 sectors, multi 16: LBA48 
Dec 26 05:30:30 ubuntu kernel: [    4.925143] ata1.01: ATA-6: ST3160021A, 8.01, max UDMA/100
Dec 26 05:30:30 ubuntu kernel: [    4.925208] ata1.01: 312581808 sectors, multi 0: LBA48 
Dec 26 05:30:30 ubuntu kernel: [    4.932472] ata1.00: configured for UDMA/100
Dec 26 05:30:30 ubuntu kernel: [    4.948547] ata1.01: configured for UDMA/100

```

This is just telling where the hdd are and what they are. 

This is the error I get, specifically with the 160 GB 

```
Dec 26 05:30:30 ubuntu kernel: [   53.185084] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec 26 05:30:30 ubuntu kernel: [   53.185155] ata1.01: BMDMA stat 0x64
Dec 26 05:30:30 ubuntu kernel: [   53.185215] ata1.01: cmd 25/00:08:00:9e:a1/00:00:12:00:00/f0 tag 0 dma 4096 in
Dec 26 05:30:30 ubuntu kernel: [   53.185218]          res 7f/7f:7f:7f:7f:7f/01:01:01:01:7f/7f Emask 0x2 (HSM violation)
Dec 26 05:30:30 ubuntu kernel: [   53.185354] ata1.01: status: { DRDY DF DRQ ERR }
Dec 26 05:30:30 ubuntu kernel: [   53.185409] ata1.01: error: { UNC IDNF ABRT }
Dec 26 05:30:30 ubuntu kernel: [   53.185497] ata1: soft resetting link

```

Is it a kernel issue?

This is from the Live CD. And this is persistent in all the updated kernels as well.

---

### Post by Hobgoblin on 2008-12-26
Are they on the same IDE cable?

Are you using master/slave or cable select?

Try some different combinations, see if it changes anything.

---

### Post by ShirishAg75 on 2008-12-26
They are on the same cable and using cable select.

BIOS shows 80 GiB as IDE0

and 160 GiB as IDE1.

---

