---
title: "Raid support for MSI 790FX-GD70"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by eekie on 2009-09-04
I have moved my MSI K9N2-platinum to my spare computer and have bought a MSI 790FX-GD70 + AM3 processor + DDR3 memory. The old mobo is provided with a nvidia chip the new one with an AMD-ATI chip
I had windows 7 and ubuntu installed on striping disks and I kept the disks. I managed to keep the old partitioning (devmapper_nvidia...) and put back a system backup of windows 7. Unfortunately I did not have an ubuntu backup, so I had to reinstall.
Neither the ubuntu live cd with dmraid installed nor the alternate cd can see the raid partitions, just two separate empty disks. Is the AMD-ATI chip not supported by ubuntu or should I have formatted the striped disks? To date I did not take the risk of crippling the restoration of my windows backup by reformatting

---

### Post by ronparent on 2009-09-07
What results do you get when you run **sudo dmraid -d**? dmraid should discover valid meta data written to those raid drives, providing it was written by a supported raid controller.

---

### Post by eekie on 2009-09-15
hello Ronparent

I have formatted the entire Raid disk. The problem is solved now
Thanks

---

