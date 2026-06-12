---
title: "Can't get SD card reader to work"
date: 2009-11-23
forum: Hardware
---

### Post by sebastianfaunes on 2009-11-23
Hi all,

I've just switched from windowsXP to ubuntu NBR. So, far it's been a great experience. Nevertheless, I am hopelessly lost on how to get my onboard SD card reader to work. It's one of those multi-card readers. I am not sure what to download, or what will solve my problem. 

I went to [http://kmuto.jp/debian/hcl/index.rhtmlx](http://kmuto.jp/debian/hcl/index.rhtmlx)   and got this hardware report I'm not sure what could be my SD reader, and how to get it operational. Best Regards, Seb:

PCI IDWorks?VendorDeviceDriverKernel       808627acYesIntel CorporationMobile 945GME Express Memory Controller Hubintel-agpv2.6.25-       808627aeYesIntel CorporationMobile 945GME Express Integrated Graphics Controllerintelfbv2.6.28-       808627a6
Intel CorporationMobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller

      808627d8YesIntel Corporation82801G (ICH7 Family) High Definition Audio Controllersnd-hda-intelv2.6.25-       808627d0
Intel Corporation82801G (ICH7 Family) PCI Express Port 1

      808627d2
Intel Corporation82801G (ICH7 Family) PCI Express Port 2

      808627c8
Intel Corporation82801G (ICH7 Family) USB UHCI Controller #1

      808627c9
Intel Corporation82801G (ICH7 Family) USB UHCI Controller #2

      808627ca
Intel Corporation82801G (ICH7 Family) USB UHCI Controller #3

      808627cb
Intel Corporation82801G (ICH7 Family) USB UHCI Controller #4

      808627cc
Intel Corporation82801G (ICH7 Family) USB2 EHCI Controller

      80862448YesIntel Corporation82801 Mobile PCI Bridgei810_rng,hw_random
      808627b9YesIntel Corporation82801GBM (ICH7-M) LPC Interface BridgeiTCO_wdt,intel-rngv2.6.25-       808627c4YesIntel Corporation82801GBM/GHM (ICH7 Family) SATA IDE Controllerata_piixv2.6.25-       808627daYesIntel Corporation82801G (ICH7 Family) SMBus Controlleri2c-i801v2.6.25-       10ec8136YesRealtek Semiconductor Co., Ltd.RTL8101E/RTL8102E PCI Express Fast Ethernet controllerr8169v2.6.25-

---

### Post by sebastianfaunes on 2009-12-04
Got it to work ha ha!!! It was as simple as rebooting with the SD card in the drive, and now it detects in no prob. Hope this helps someone else!!

---

