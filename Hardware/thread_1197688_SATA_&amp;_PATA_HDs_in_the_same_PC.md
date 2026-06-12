---
title: "SATA &amp; PATA HDs in the same PC?"
date: 2009-06-26
forum: Hardware
---

### Post by siabost on 2009-06-26
Hi,

I bought a CCL1010 (AMD Athlon 64 7750 2.7Ghz) Desktop - [http://www.cclonline.com/product-inf...oduct_id=20052](http://www.cclonline.com/product-inf...oduct_id=20052) The PC was supplied without an OS. I've since loaded Ubuntu 9.04.

The hard drive in the unit is a SATA type and I would like to install a 2nd (data only) 320GB IDE PATA Hard Drive which I bought for another machine.

The CCL1010 has a ribbon connector & power cable for an extra IDE unit. Making sure that the IDE HD was set to slave on the jumpers, I connected it up. Checking in the BIOS, both HDs were recognised correctly as master & slave. The only other IDE unit in the case is a DVD Rewriter.

I did all this before installing the OS but with the IDE HD connected the I could not boot from the DVD unit - necessary for installation of the OS. The message came up that there was no bootable CD in the drive (as if it was trying to boot from the IDE HD).

I checked the boot order in the BIOS & again that seemed OK.

With the IDE HD disconnected the PC would boot from the DVD Drive.

What am I missing?

Any help greatly appreciated.

---

### Post by siabost on 2009-06-28
Turns out conflicts can be brought about if IDE Optical Drives & IDE Hard Drives are combined on the same IDE cable/header: normally you would have at least two headers - one for HDs & one for ODs.

I have ordered a PATA to SATA data cable adapter which should allow connection of my IDE OD via the spare SATA connector on my motherboard.

Still to figure out whether the IDE drive should be Master, Slave or Cable Select, but progress has been made anyhow.:D

---

### Post by jocko on 2009-06-28
> **siabost said:**
> The CCL1010 has a ribbon connector & power cable for an extra IDE unit. Making sure that the IDE HD was set to slave on the jumpers, I connected it up. Checking in the BIOS, both HDs were recognised correctly as master & slave. The only other IDE unit in the case is a DVD Rewriter.

...

What am I missing?

Any help greatly appreciated.
Why did you connect the ide hard drive as slave? Master/slave only applies to devices connected to the same ribbon cable, so unless it's connected on the same ribbon cable as the dvd, it must be set as master. (even if they are on the same cable, I think it's probably better to have the hd as master and dvd as slave, but I don't think it's a very good idea to have a hard drive and a dvd connected to the same cable, as the transfer rate is probably going to be set by the slower dvd, which will probably cause problems).

---

