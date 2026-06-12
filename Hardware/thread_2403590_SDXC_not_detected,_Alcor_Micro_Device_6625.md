---
title: "SDXC not detected, Alcor Micro Device 6625"
date: 2018-10-13
forum: Hardware
---

### Post by salseng on 2018-10-13
Hi, 

I am using HP Envy laptop, ditched windows 10 in favor of Ubuntu 18.04 LTS.

For the last couple of months, I have not been able to mount any microSD cards. My microSD reader is probably PCI based Alcor Micro Device 6625. 

can anyone help me solve this problem? I have attached lspci: 


00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 02)
00:08.0 System peripheral: Intel Corporation Skylake Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Unassigned class [ff00]: Alcor Micro Device 6625
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)

---

### Post by Yellow Pasque on 2018-10-15
[https://github.com/linuxhw/HWInfo](https://github.com/linuxhw/HWInfo)
[https://wikidevi.com/wiki/Alcor_Micro_AU6601](https://wikidevi.com/wiki/Alcor_Micro_AU6601)
Given that the Alcor 6625 has no driver loaded in 100% of reports received, it does not look hopeful.

---

