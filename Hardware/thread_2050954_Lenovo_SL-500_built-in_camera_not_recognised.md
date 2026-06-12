---
title: "Lenovo SL-500 built-in camera not recognised"
date: 2012-08-31
forum: Hardware
---

### Post by ajeannotte on 2012-08-31
my issue is that in any version of ubuntu i've put on my laptop over the last few years, none of them have recognised the built-in webcam. it's as if the hardware doesn't exist. 

no issue with the camera in windows (dual boot).


the laptop is a:

Lenovo Thinkpad SL-500

it's about 4 years old now.


i've tried posting on other camera issue posts, was told to produce my own post as different laptops might have different issues. 

here's a dump of what i was asked to produce on the last post

```
Laptop:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
	Subsystem: Lenovo Device [17aa:20e0]
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
	Subsystem: Lenovo Device [17aa:20f0]
	Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
	Subsystem: Lenovo Device [17aa:20f0]
	Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
	Subsystem: Lenovo Device [17aa:20f0]
	Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
	Subsystem: Lenovo Device [17aa:20f1]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
	Subsystem: Lenovo Device [17aa:20f2]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
	Subsystem: Lenovo Device [17aa:20f0]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
	Subsystem: Lenovo Device [17aa:20f0]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
	Subsystem: Lenovo Device [17aa:20f0]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
	Subsystem: Lenovo Device [17aa:20f1]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
	Subsystem: Lenovo Device [17aa:20f6]
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
	Subsystem: Lenovo Device [17aa:20f8]
	Kernel driver in use: ahci
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G98 [GeForce 9300M GS] [10de:06e9] (rev a1)
	Subsystem: Lenovo Device [17aa:2107]
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
0c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Lenovo Device [17aa:2108]
	Kernel driver in use: r8169
	Kernel modules: r8169
0d:00.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
	Subsystem: Lenovo Device [17aa:2109]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
0d:00.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
	Subsystem: Lenovo Device [17aa:210a]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
0d:00.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
	Subsystem: Lenovo Device [17aa:210c]
	Kernel driver in use: r592
	Kernel modules: r592
0d:00.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
	Subsystem: Lenovo Device [17aa:210d]
	Kernel driver in use: r852
	Kernel modules: r852
Laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:2145 Broadcom Corp. Bluetooth with Enhanced Data Rate II
Bus 005 Device 003: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
```

it seems a bit foolish to need to either log on through windows or plug in a usb camera in order to skype when there is a camera built in.

any help?

---

### Post by offgridguy on 2013-01-26
> **ajeannotte said:**
> my issue is that in any version of ubuntu i've put on my laptop over the last few years, none of them have recognised the built-in webcam. it's as if the hardware doesn't exist. 
I have found the same, not just with ubuntu but other distro's as well,
however i just install one of the webcam apps.available in the software
center.  So far that has done it, don't know about video though as i don't use it.:)

---

