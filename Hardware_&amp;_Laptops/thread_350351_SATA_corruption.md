---
title: "SATA corruption"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by daverave999 on 2007-01-31
I've been having seemingly continuous problems with corruption on my two SATA drives. I'm pretty sure it's not the drives as they are both newish, and I find it unlikely that they are both dying at the same time (I realise it's not impossible though...) I've tried different cables and it seems to make no difference. I've updated the BIOS, and also clocked the memory down to make sure it wasn't that (not OC'd, just lowered to eliminate another possibility).

I'm using the onboard SATA controller (Via VT8237) and google tells me that this might be a problem. Would turning off write-caching possibly fix this, and if I did would I suffer much loss of performance?

Recommendations for a SATA card that works well in linux would also be gratefully received, as I currently have 640 gig of storage space that I daren't trust. :(

Any other suggestions would be appreciated.

TIA

---

### Post by RandomJoe on 2007-01-31
I don't have any experience with that chipset...

I have two SATA setups here - one is a 4-disk RAID5 attached to a Promise SATAII 150 TX4 PCI card.  (It isn't a HW RAID card, I'm using the kernel's software RAID.)  The others are on a motherboard's nVidia nForce4 chipset, don't think you'd find that on an add-in card.  Both work fine, though.  Promise offers a variety of configurations, of course, besides that one.

---

