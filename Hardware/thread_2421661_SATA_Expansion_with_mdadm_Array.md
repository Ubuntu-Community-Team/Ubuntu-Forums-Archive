---
title: "SATA Expansion with mdadm Array"
date: 2019-06-25
forum: Hardware
---

### Post by wischrendel on 2019-06-25
Hey Everyone, I currently have a server with four 4TB drives in a raid 5 array using mdadm. I have one more SATA port left on my motherboard but I intend to add at least 2-4 new drives in the next month. I would like to expand my SATA ports with a 4-6 port PCI Expansion card, add those additional drives, and then add them to my array. I was doing a little research and found that these cards have read/write limits. My thinking may be entirely flawed as I do not fully understand hardware limits, but could this potentially cause problems with my array since some the ports (PCI and regular) have different data throughput? I would have 6 drives on motherboard SATA and 4 on PCI SATA all in a raid 5 array. Would it be better to just create a second array with the PCI SATA Drives?

---

### Post by TheFu on 2019-06-26
For storage devices over 1TB in size, RAID5 is NOT a best practice. 
Recommended solutions:
* RAID6
* switching to ZFS RAIDz2
* RAID1
* RAID10
Probably best to keep similar performing disks in the same storage pool, but really I don't think spinning disk performance really comes close to mattering regardless of the interface, assuming you don't go crazy and use USB ports. Hint - don't.

IMHO.

---

