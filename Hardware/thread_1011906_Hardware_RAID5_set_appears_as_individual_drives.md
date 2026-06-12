---
title: "Hardware RAID5 set appears as individual drives"
date: 2008-12-15
forum: Hardware
---

### Post by orangejon on 2008-12-15
I'm trying to install Ubuntu 8.10 onto a blank three-disk hardware RAID5 array.  The 3 x 1TB drives are connected to a Silicon Image 3114 SATA card.

I used the RAID Configuration Utility to do a "Quick Low Level Format" on each drive, then created a RAID5 set including all three drives.  The "Logical Drive" section of the screen now displays "SiI Raid5 Set - 1863Gb".  Similar information is displayed during boot.  This looks fine, as far as I can see.

However, when I boot from the Ubuntu 8.10 CD and get to the drive configuration step, all three drives are displayed individually (sda, sdb, sdc).  I would have expected them to be displayed as a single drive.

Any ideas how I can fix this?

Thanks in advance,

Jon

---

### Post by Fire_Chief on 2008-12-15
Could you provide more information on the "RAID Configuration Utility" you used to create the RAID set? The product information I'm reading from the Silicon Image website indicates that the 3114 is not a hardware RAID chipset but just a simple SATA controller.[http://www.siliconimage.com/products/product.aspx?id=28]("http://www.siliconimage.com/products/product.aspx?id=28")

If this is the case, you won't have the ability to do hardware RAID with the drives (thus why you are seeing all 3 in Ubuntu setup).

Cheers!

[EDIT] - It does appear that the controller does some form of RAID though I'm not convinced it's totally hardware RAID. It states specifically in the manual for the 3114 that it supports RAID 0, 1, and 10.

---

### Post by orangejon on 2008-12-15
Thanks for your fast reponse, Fire_Chief, it's most appreciated :)

I was led to believe when purchasing the card that it supported RAID5, and the "Configuration Utility" (i.e. the BIOS-thing built into the card that you can access during boot) allowed me to (apparently) create a Raid5 set.

The manual from Asus for the same chip does talk about RAID5 support: [http://support.asus.com/technicaldocuments/Sil3114.pdf](http://support.asus.com/technicaldocuments/Sil3114.pdf)

So I'm a bit confused now.

---

### Post by orangejon on 2008-12-15
[This page]("http://linuxmafia.com/faq/Hardware/sata.html#sil") seems to suggest that in fact this card doesn't support hardware RAID at all, and I've been thoroughly duped.  It also seems that real hardware RAID cards are universally expensive (£100+).

So it looks like I'll be resorting to slow software RAID again then.. :(

---

