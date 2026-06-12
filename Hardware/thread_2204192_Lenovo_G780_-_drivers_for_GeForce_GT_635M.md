---
title: "Lenovo G780 - drivers for GeForce GT 635M"
date: 2014-02-07
forum: Hardware
---

### Post by kontakr on 2014-02-07
Hi there!


I have laptop Lenovo G780 with hydryb graphic card Intel and GeForce GT 635M. My ubuntu uses only Intel's cart. I have installed GeForce 332.21 driver on win7 and it works fine. I tried to install this drivers: [http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/) but no success. I also installed bumblebee and bumblebee-nvidia, rebooted laptop, but ubuntu still cannot find Nvidia graphic card. lspci says:
> 00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 635M] (rev ff)
02:00.0 Ethernet controller: Qualcomm Atheros AR8162 Fast Ethernet (rev 10)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)


I tried to install the drivers from nvidia website, but an error occures. I do not know what to do now. How can i install the correct drivers?

---

