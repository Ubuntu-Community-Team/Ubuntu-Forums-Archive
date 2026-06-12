---
title: "SAS HBA that enumerates drives in Linux in the same order as the topology"
date: 2016-03-04
forum: Hardware
---

### Post by Chris_Beasley on 2016-03-04
Hi,

I'm currently running a number of LSI 9211-8is as part of my custom mdadm setup. I've hit the snag that the drives enumerate using the SAS WWAN rather than in the order they're detected by the OS; e.g.

Physical Slot 1 = SAS Topology Port 0 = sdb
Physical Slot 2 = 
SAS Topology Port 1 = sdf
etc.

The LSIs cannot be made to recognise that I want the slot 1 to actually be sda and this won't change according to LSI support.

So, what I am looking for is advice on what SAS HBAs (6GB/S or more) support the following setup;

Physical Slot 1 = SAS Topology Port 0 = sda
Physical Slot 2 = SAS Topology Port 1 = sdb
etc.

I've found that the Adaptec HBA 1000-16i (12G SAS) appears to do this fine, but that is rather expensive here in NZ ($600NZD) so I'm looking for alternatives. It must have a minimum of 8 ports and support >4TB drives.

Am I likely to only use the Adaptec HBA 1000-16i, or are there any more?

Any help is appreciated!

Chris

---

### Post by SeijiSensei on 2016-03-04
Can you use UUIDs instead of device names?  What is the result of running "sudo blkid"?

---

