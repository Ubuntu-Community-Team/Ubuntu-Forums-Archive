---
title: "SIIG SATA 150 PCI Card Not Working in Ubuntu 7.04"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by RAdams on 2007-05-26
I'm trying to install Ubuntu on a friend's computer. He just bought a SATA 150 PCI controller from SIIG. The card has its own BIOS which runs at POST, and Ubuntu detects the drive just fine. However, gParted froze up while trying to make an ext3 partition on the drive. I ran mkfs.ext3 /dev/sdc and the process stopped while writing the inodes table. I also tried using gParted (doesn't make a difference, I know -- it uses the same command). It just can't format this drive.

Is anyone aware of any problems with this controller? I've already checked the hard drive in another box; it formats fine there. What do you suggest?

---

