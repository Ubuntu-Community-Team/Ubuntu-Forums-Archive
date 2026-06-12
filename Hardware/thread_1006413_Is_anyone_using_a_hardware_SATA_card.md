---
title: "Is anyone using a hardware SATA card?"
date: 2008-12-09
forum: Hardware
---

### Post by supchaka on 2008-12-09
I'm thinking of picking up an adaptec SATA card. My file transfers are atrocious. I'm getting like 5mb transfers from disk to disk or disk to USB. 

I'm using a Seagate 320gb and a WD 400gb. Ive tried the 3 modes, IDE RAID and AHCI in my bios, none of them made any difference. The only other thing I can think of is my software driven raid controller on the motherboard. One other thing that irritated me about my controller is that I wasnt able to Acronis the system because the hard drives didnt load before their software. I've never been too fond of them. 

So I was wondering if anyone is using a SATA card has any complaints about it or can verify they are getting solid file transfers?

---

### Post by mk1w86 on 2008-12-09
I have successfully used SATA cards with SIL3114 chipsets.  These are PCI so you will only get 1.5GBPS (as opposed to 3GBPS with PCI-E) and have 4 ports.

The performance of the drives seem fine.

These cards can be flashed with a RAID firmware or a normal IDE firmware.

I use the normal IDE firmware with two 320GB Seagate drives in software RAID 1. :)

---

### Post by Platypus123 on 2009-07-16
I have a PCI card with the Sil3114 chipset, but it's not a true hardware raid card (fakeraid).  I'm not sure if any true hardware raid cards use this chipset.

---

