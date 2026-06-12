---
title: "Block pata_sil680 driver from loading"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by Rick's Fork on 2007-10-28
I have a RAID controller based on the Silicon Image 0680 chipset which I believe uses the pata_sil680 driver.  The array type on this controller is not supported under Ubuntu but the driver tries to mount each drive in the array as a single drive and slows down the boot process by several minutes.  I would like to keep the driver for the controller from loading.

I had the same problem in Edgy and was able to resolve the problem - unfortunately I don't remember exactly what I did.  I think I blacklisted the driver somehow since when I do an lsmod in Edgy the driver is not listed.

I think this is what I need to do in Gutsy but I can't seem to get it to work.  I've added the line:

blacklist pata_sil680

to the blacklist files *blacklist-ata* and *blacklist* at /etc/modprobe.d but it still loads the driver.  It this the right way to do this or should I take a different approach?  Any thoughts or suggestions would be appreciated.  Thanks,

---

### Post by Rick's Fork on 2007-11-01
I think the reason the blacklist doesn't work is that the pata_sil680 driver is embedded in the kernel in Gutsy.  So now I think I need to re-compile the kernel without this driver/module (pata_sil680.ko) embedded.  Does this sound right?  If so, how would I do this in Gutsy?  Thanks again for any help or suggestions.

---

