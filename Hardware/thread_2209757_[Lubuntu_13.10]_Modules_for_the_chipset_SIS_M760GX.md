---
title: "[Lubuntu 13.10] Modules for the chipset SIS M760GX + 964L"
date: 2014-03-07
forum: Hardware
---

### Post by balubeto on 2014-03-07
Hi

I have an Asus notebook A6K-Q015H with chipset SIS M760GX + 964L. 

I would like to know what packages-modules I should install in order to completely manage this chipset in Lubuntu 13.10 32-bit.

Thanks

Bye

---

### Post by mörgæs on 2014-03-07
Here's some advice:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464)

---

### Post by balubeto on 2014-03-07
> **mörgæs said:**
> Here's some advice:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464)

In practice, when I will have to format this computer, what should I do to properly recognize all the components of the motherboard with this chipset?

Thanks

Bye

---

### Post by Yellow Pasque on 2014-03-07
Most of the drivers are built into the kernel, so you shouldn't need to do anything special to have a working system. Optionally, you can install a patched version of the sis video driver to enable 2D acceleration. [https://launchpad.net/~dtl131/+archive/mediahacks/](https://launchpad.net/~dtl131/+archive/mediahacks/)

---

### Post by balubeto on 2014-03-07
> **Temüjin said:**
> Most of the drivers are built into the kernel, so you shouldn't need to do anything special to have a working system. Optionally, you can install a patched version of the sis video driver to enable 2D acceleration. [https://launchpad.net/~dtl131/+archive/mediahacks/](https://launchpad.net/~dtl131/+archive/mediahacks/)

After entering the repository on my list, what are the packages that I have to download to make sure that my chipset is fully working in all its functions?

Thanks

Bye

---

### Post by balubeto on 2014-03-10
The problem is this:

From this LXDE screen, I see:

[http://i58.tinypic.com/2q2k8pf.png](http://i58.tinypic.com/2q2k8pf.png)

So, how do I to understand what is that unknown component?

Thanks

Bye

Note: If I install the package kernel-source-bcmwl, the wireless chip does not work, and it prevents the Linux reboot. How come?

---

### Post by Yellow Pasque on 2014-03-10
Oh, so you have nvidia graphics and are not using SiS integrated graphics? Then you really don't need my PPA...

> So, how do I to understand what is that unknown component?
Well, you can look at lspci and lsusb output:
```
sudo update-pciids
sudo update-usbids
lspci -k
lsusb
```

---

### Post by balubeto on 2014-03-10
> **Temüjin said:**
> Oh, so you have nvidia graphics and are not using SiS integrated graphics? Then you really don't need my PPA...


Well, you can look at lspci and lsusb output:
```
sudo update-pciids
sudo update-usbids
lspci -k
lsusb
```

The **lspci -k** output is:

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] Device 0756 (rev 02)
 Subsystem: ASUSTeK Computer Inc. Device 1977
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
 Kernel driver in use: pcieport
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] LPC Controller (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller (rev 01)
 Subsystem: ASUSTeK Computer Inc. Device 1107
 Kernel driver in use: pata_sis
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
 Subsystem: ASUSTeK Computer Inc. Device 1816
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
 Subsystem: ASUSTeK Computer Inc. Device 1103
 Kernel driver in use: snd_intel8x0
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
 Subsystem: ASUSTeK Computer Inc. Device 1107
 Kernel driver in use: ohci-pci
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
 Subsystem: ASUSTeK Computer Inc. Device 1107
 Kernel driver in use: ohci-pci
00:03.2 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
 Subsystem: ASUSTeK Computer Inc. Device 1107
 Kernel driver in use: ohci-pci
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
 Subsystem: ASUSTeK Computer Inc. Device 1107
 Kernel driver in use: ehci-pci
00:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
 Subsystem: ASUSTeK Computer Inc. A6U notebook embedded card
 Kernel driver in use: b43-pci-bridge
00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
 Subsystem: ASUSTeK Computer Inc. Device 1107
 Kernel driver in use: yenta_cardbus
00:0a.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
 Subsystem: ASUSTeK Computer Inc. Device 1977
 Kernel driver in use: firewire_ohci
00:0a.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
 Subsystem: ASUSTeK Computer Inc. Device 1977
 Kernel driver in use: sdhci-pci
00:0a.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
 Subsystem: ASUSTeK Computer Inc. Device 1977
 Kernel driver in use: r592
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
 Subsystem: ASUSTeK Computer Inc. L8400B or L3C/S notebook
 Kernel driver in use: 8139too
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
 Kernel driver in use: k8temp
01:00.0 VGA compatible controller: NVIDIA Corporation NV44M [GeForce Go 6200] (rev a1)
 Subsystem: ASUSTeK Computer Inc. Device 188a
 Kernel driver in use: nvidia

```

and the **lsusb** output is:

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 062a:0201 Creative Labs Defender Office Keyboard (K7310) S Zodiak KM-9010
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

What there is that does not work?

Thanks

Bye

---

### Post by Yellow Pasque on 2014-03-11
It's probably the modem, since it does not have a driver/kernel module:
```
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
```

---

### Post by balubeto on 2014-03-12
> **Temüjin said:**
> It's probably the modem, since it does not have a driver/kernel module:
```
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
```

So, what package I need to download for running properly this analog modem?

Thanks

Bye

---

