---
title: "Onboard audio not working"
date: 2020-02-04
forum: Hardware
---

### Post by ra7411 on 2020-02-04
The onboard audio on one of my desktops has stopped working. The pci-e CM8738 audio card works fine.
It's a Ryzen cpu machine, I'm running kernel 5.3.0-050300.

( ub 18.04,   cpu  AMD Ryzen 3 3200G with Radeon Vega Graphics, Motherboard B450 TOMAHAWK (MS-7C02) Micro-Star International Co., Ltd )

I've included the lspci output and pics of what the Pulse Configuration tab shows. 

The only thing I can think of is that the onboard audio is being sent to a nonexistent HDMI speaker (the machine has an HDMI monitor but no HDMI speakers).

Any ideas how to get the onboard audio working?

Thanks

```
 
 root@ra-main:~# lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15d0
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 15d1
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:01.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15d3
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15db
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15dc
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15e8
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15e9
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ea
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15eb
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ec
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ed
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ee
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ef
12:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 43d5 (rev 01)
12:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] Device 43c8 (rev 01)
12:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c6 (rev 01)
20:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c7 (rev 01)
20:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c7 (rev 01)
20:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c7 (rev 01)
20:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c7 (rev 01)
20:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43c7 (rev 01)
22:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
27:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 04)
28:00.0 Multimedia audio controller: C-Media Electronics Inc CMI8738/CMI8768 PCI Audio (rev 10)
28:00.1 Communication controller: C-Media Electronics Inc CM8738 (rev 20)
2a:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Picasso (rev c9)
2a:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 15de
2a:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 15df
2a:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15e0
2a:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15e1
2b:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 61)
root@ra-main:
 
```

---

### Post by mörgæs on 2020-02-05
Lately you have posted frequently about problems for this install. I think it's time to let go of 18.04 and do a fresh install of 19.10.

---

### Post by Yellow Pasque on 2020-02-05
Your lspci doesn't appear to show any motherboard audio. It shows your discrete sound card and the HDMI audio that's built into the CPU. Are you sure it's enabled in the BIOS?
Also, please run (sudo) update-pciids before showing lspci out for newer hardware. It will make things more human-readable.

---

