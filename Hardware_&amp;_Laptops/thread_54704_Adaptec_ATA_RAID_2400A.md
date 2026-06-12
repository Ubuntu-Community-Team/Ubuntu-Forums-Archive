---
title: "Adaptec ATA RAID 2400A"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by dustyculler on 2005-08-05
I'm setting up a new server with an Adaptec ATA RAID 2400A and an AMD Athlon 64 X2 4200+.  The raid card uses the dpt_i2o driver in 32-bit mode and is detected as such allowing me to install onto this card.  Hoary i386 works great with this card.

However when I try to install Hoary amd64, the card is not recognized at all as far as I can tell.  I've talked to Adaptec about this and they claim that there are kernel patches that have been sent that are mostly being ignored to get this driver into the kernel w/ 64-bit support.  They did recommend using the open source i2o driver.

My first question is if there is a way to tell the Hoary amd64 installer to use this driver (if it is indeed included on the installer) allowing me to install on to the raid array?

My second question is where the appropriate place would be to ask for this to be the default behaviour in Breezy?

I bought this cpu to use both cores and the NX bit, which it looks like neither can be used in 32-bit mode, so I really want to use the amd64 version.

Thanks in advance.

---

