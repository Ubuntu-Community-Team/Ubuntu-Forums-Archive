---
title: "edac sbridge error on boot"
date: 2013-08-21
forum: Hardware
---

### Post by PendragonUK on 2013-08-21
Every time my system boots there is a pause, two lines of text appear briefly. Something about "edac sbridge error" then disabling it. After this timeout the boot continues.

Ubuntu Gnome 13.04
3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

System Hardware:
Processor: Intel Core i7-3930K @ 3.20GHz (12 Cores), Motherboard: MSI X79A-GD45 (8D) (MS-7760) v2.0, Chipset: Intel Xeon E5/Core, Memory: 16384MB, Disk: 256GB M4-CT256M4SSD2 + 1000GB Western Digital WD1002FAEX-0, Graphics: AMD Radeon HD 7900 3072MB, Audio: Realtek ALC892, Monitor: PL2773HD, Network: Intel 82579V Gigabit Connection

---

### Post by tinman2 on 2014-06-22
[QUOTE=PendragonUK;12763953]Every time my system boots there is a pause, two lines of text appear briefly. Something about "edac sbridge error" then disabling it. After this timeout the boot continues.

Ubuntu Gnome 13.04
3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

  Seriously, no one has answered this question after all this time???
  I have the same problem on Ubuntu 14.04 LTS.  I never had this problem under Ubuntu 13.  Nothing is broken that I know of on my system, just get the same two lines flash by on booting up and everything runs just fine.

System: Marquis C528-T Workstation 
     Intel DX79TO ATX motherboard, X79 Express
     Onboard Realtek 6-channel (5.1) High Definition audio
     Onboard Intel PCI Express Gigabit Ethernet controller
     2xPCI-E x16 v3, 3xPCI-E x1, 1x32-bit/33Mhz PCI slots
     2xUSB 3.0 ports, 6xUSB 2.0 ports, 1xIEEE-1394a port
     1 x Intel Core i7-4820K (Ivy Bridge E) 3.7 Ghz, 3.9 Ghz Turbo 10MB L3, Socket 2011, 4-core, 22nm, 130W
     4 x Samsung 4GB DDR3-1600 unbuffered, non-ECC module
     1 x Western Digital Caviar Black WD5003AZEX 500GB, 7200rpm, SATA 6Gbs, 64MB cache
     ASUS DRW-24B1ST-BLK 24xDVD+-R,8xDVD+RW,6xDVD-RW,12xDVD+R DL,4x DVD-R DL,48xCDR,32xCDRW,48xCDROM,16xDVDROM,Serial ATA, 2MB, Black (bare drive)
     ASUS GT630-2GD3 GeForce GT 630 (Fermi),PCI-E x16,2GB DDR3,1xDVI-I,1xHDMI,1xDB-15,Dual Head
     Mid Tower Chassis (SR209), SAS enclosure (SAS6G/4 hotswap HD), 1x12cm, 1x9cm,600W ATX12V PS (80 Plus), Active PFC, Black
Ubuntu 14.04 LTS

---

### Post by Yellow Pasque on 2014-06-22
It's a common diagnostic message: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536)

Bottom line: Unless you have ECC RAM, the warning is harmless (albeit annoying) and you can safely ignore it.

---

### Post by tinman2 on 2014-06-23
Thank you Juan, you da man!  ;)

---

