---
title: "Lenovo Y500 Sub woofer not working."
date: 2010-10-27
forum: Hardware
---

### Post by rubal on 2010-10-27
I am using lenovo Y500 4EQ bt hav a major problem with my sub woofer. its not working with any ditro of ubuntu using alsa. i made it work on jaunty 9.04 using oss bt still i cant be a permanent solutions as that solution is not woking with any later editions of Ubuntu(Ubuntu 9.10 ,Ubuntu 10.04 and Ubuntu 10.10).

Does anyone know hw can i make my sub woofer working ,because without it sound is very low...
Plzzz help i really need it urgently....:(

Thanks In Advance.

---

### Post by lxapp on 2010-12-11
I'm facing the same problem with my Lenovo Y500 on Ubuntu 10.04. I think in my system alsa manages sound instead of oss.Could someone suggest some solution?

I'm posting lspci
```


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

---

### Post by rubal on 2010-12-19
I had tired to work out with oss also, but it will work with jaunty(ubuntu 9.04) not with any later release. By default sound controller is alsa but surbwoofer never work with it. :(

Now just can wait for the ubuntu developer team to remove this bug in Upcoming releases or provide any resonable solution.

Waiting waiting and waiting....

---

