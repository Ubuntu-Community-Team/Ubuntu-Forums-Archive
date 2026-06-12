---
title: "mdadm with onboard and raid card"
date: 2010-07-26
forum: Hardware
---

### Post by canabal on 2010-07-26
Hey guys,

I was just curious if any of you have experience with this.

I have recently built myself a media server with 3x2tb drives in a raid 5 mdadm setup.  I also have 1 hard drive not in the mdadm setup for the OS (just in case I need to change it, the storage can stay).

Unfortunately, I did not think ahead and my server only has 4 sata ports.  I am wondering if it is possible to purchase a raid card/sata card (pci) and would that allow me to add more hdds to my mdadm setup or can you not combine built in and those on a raid/sata card.

Thanks in advance

---

### Post by jacekk015 on 2010-07-27
You can use additional SATA card, but take in mind that for example 4 SATA ports on 1 PCI-E slot will be limited by the PCI-E speed.

---

### Post by canabal on 2010-07-27
> **jacekk015 said:**
> You can use additional SATA card, but take in mind that for example 4 SATA ports on 1 PCI-E slot will be limited by the PCI-E speed.
Perfect, thanks for the help, that is what I expected.  Thankfully it is just a storage server, so speed is not an issue.

---

