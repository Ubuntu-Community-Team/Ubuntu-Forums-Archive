---
title: "Upgrading from RAID 1 to RAID 0+1 / 1+0"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by KrisWillis on 2007-07-09
I'm currently running my install of Feisty on two 80GB discs hooked up to a "Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller", as reported by *lspci*.

The card is currently configured as a RAID 1 array (mirrored), though, as the card can take 4 discs, and I have another two 80GB discs sitting around, I was thinking about converting to a 0+1 or 1+0 array to add a bit more space and performance.

The bit I'm not so sure about is reconfiguring the card. Would it just be the case of adding the two extra discs, hitting F3 on boot to jump into the RAID config and then reconfiguring? Is there likely to be any issues when booting back into Feisty because of the difference in disc size? Would it mess with the partition information?

Any help would be great, many thanks.

---

### Post by Soybean on 2007-07-09
In general, reconfiguring a hardware RAID involves wiping the disks. The RAID controller works on a lower level than partitions and file systems... it would likely be possible to make a really smart RAID controller that could keep your files intact across a switch, but I don't think it would be very practical.

---

### Post by KrisWillis on 2007-07-09
I guess that makes sense. Because the RAID card built my RAID 1 array from a single disc, I was under the illusion that it would split the data from the source disc and write half of it to the other stripe disc then mirror both of them onto the other two. But the more I think about it now, thats not going to happen, is it! After all, RAID 1 is just mirroring a disc, RAID 0 is more the organisation of data...

Thanks Soybean.

---

