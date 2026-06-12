---
title: "youtube crashing/ati display driver"
date: 2008-08-09
forum: General Help
---

### Post by rudolphna54 on 2008-08-09
ok... couple things all related.  First of all, when i watch a youtube video, partway through it the whole computer just locks, and about 1 second of sound is looped, and i have to manually restart to resolve it. However, this keeps happening. I read it may be the ati driver 
(System is.....
Gateway 832GM (Intel D915GSE mobo)
Intel Pentium 4 630
2GB PC2700 DDR 
Sapphire ATi Radeon HD 2600XT (512 GDDR3) PCIe 16x
Western Digital 250GB SATA
Windows XP MCE/Ubuntu 8.04
Gigabyte PCI Wireless LAN adaptor

So i downloaded the latest display driver from ATi (8.7) however i am unable to install it, for some reason i cannot find it in synaptics, would anyone be able to assist me so this does not happen? Thanks. :)

---

### Post by PmDematagoda on 2008-08-09
When you download the fglrx driver from the ATi web site you cannot install it through Synaptic, although the fglrx driver is in the repositories, so just search for fgrlx in Synaptic or do:-
```
sudo apt-get install xorg-driver-fglrx
```

---

