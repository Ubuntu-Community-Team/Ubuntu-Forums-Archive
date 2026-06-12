---
title: "Audio problems on laptop Asus rog strick ryzen 9 7945hx nvidia 4060"
date: 2023-08-07
forum: Hardware
---

### Post by Dedalo on 2023-08-07
Hello everyone. I have just purchased this laptop Asus rog strick ryzen 9 7945hx nvidia 4060. I have installed ubuntu on it last week. I have dual boot with windows, so I'm certain that some issues are related to drivers and software problems. Until a bios update recently I made, requested by Windows, my wifi started working on ubuntu (previously worked on Windows but not in ubuntu).

However, the problem I have now is that I have no sound in ubuntu (I do have when using windows). 

When I go to sound in settings, on Output device the only output device I can choose is one that reads ''Speakers - Family 17h (Models 10h-1fh) HD audio controller. Same is for Input device for the internal microphone. 

When I go to alsamixer on terminal I see the following:

Card: HDA NVidia                                     F1:  Help               &#9474;
&#9474; Chip: Nvidia GPU a7 HDMI/DP                          F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: S/PDIF                                         Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                       &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                        &#9474;
&#9474;                       &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;                        &#9474;
&#9474;                       &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                        &#9474;
&#9474;                    < S/PDIF >S/PDIF 1 S/PDIF 2 S/PDIF 3                      &#9474;
&#9474;                                                               


When I press F6, I can see there the Nvidia card, and even edit, but it doesn't have any effect on the systems sound.

Here I give some information obtained from terminal

$ lspci | grep -i audio 01:00.1 Audio device: NVIDIA Corporation Device 22be (rev a1) 08:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor (rev 62) 08:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller


Here is the output for lspci -v:

:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14d8
    Subsystem: ASUSTeK Computer Inc. Device 14e3
    Flags: fast devsel

00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 14d9
    Subsystem: ASUSTeK Computer Inc. Device 14e3
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Capabilities: <access denied>

00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14da
    Flags: fast devsel, IOMMU group 0

00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14db (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 32, IOMMU group 1
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000f000-0000ffff [size=4K]
    Memory behind bridge: fb000000-fc0fffff [size=17M]
    Prefetchable memory behind bridge: 000000fa00000000-000000fc01ffffff [size=8224M]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:01.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14db (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 33, IOMMU group 2
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: fce00000-fcefffff [size=1M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:01.6 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14db (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 34, IOMMU group 3
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff [size=4K]
    Memory behind bridge: fcd00000-fcdfffff [size=1M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:01.7 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14db (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 35, IOMMU group 4
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: fca00000-fcbfffff [size=2M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14da
    Flags: fast devsel, IOMMU group 5

00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14db (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 36, IOMMU group 6
    Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
    I/O behind bridge: 00001000-00001fff [size=4K]
    Memory behind bridge: fc600000-fc9fffff [size=4M]
    Prefetchable memory behind bridge: 0000000860000000-00000008601fffff [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14da
    Flags: fast devsel, IOMMU group 7

00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14da
    Flags: fast devsel, IOMMU group 8

00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14da
    Flags: fast devsel, IOMMU group 9

00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14dd (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 37, IOMMU group 10
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff [size=4K]
    Memory behind bridge: fc200000-fc5fffff [size=4M]
    Prefetchable memory behind bridge: 000000fc10000000-000000fc201fffff [size=258M]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:08.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14dd (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 38, IOMMU group 11
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: fcc00000-fccfffff [size=1M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 71)
    Subsystem: ASUSTeK Computer Inc. FCH SMBus Controller
    Flags: 66MHz, medium devsel, IOMMU group 12
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
    Subsystem: ASUSTeK Computer Inc. FCH LPC Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0, IOMMU group 12

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e0
    Flags: fast devsel, IOMMU group 13

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e1
    Flags: fast devsel, IOMMU group 13

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e2
    Flags: fast devsel, IOMMU group 13

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e3
    Flags: fast devsel, IOMMU group 13
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e4
    Flags: fast devsel, IOMMU group 13

00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e5
    Flags: fast devsel, IOMMU group 13

00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e6
    Flags: fast devsel, IOMMU group 13

00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e7
    Flags: fast devsel, IOMMU group 13

01:00.0 VGA compatible controller: NVIDIA Corporation Device 28e0 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 226d
    Physical Slot: 0
    Flags: fast devsel, IRQ 255, IOMMU group 14
    Memory at fb000000 (32-bit, non-prefetchable) [disabled] [size=16M]
    Memory at fa00000000 (64-bit, prefetchable) [disabled] [size=8G]
    Memory at fc00000000 (64-bit, prefetchable) [disabled] [size=32M]
    I/O ports at f000 [disabled] [size=128]
    Expansion ROM at fc000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

01:00.1 Audio device: NVIDIA Corporation Device 22be (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 226d
    Physical Slot: 0
    Flags: bus master, fast devsel, latency 0, IRQ 99, IOMMU group 14
    Memory at fc080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

02:00.0 Non-Volatile memory controller: Micron Technology Inc Device 5413 (rev 03) (prog-if 02 [NVM Express])
    Subsystem: Micron Technology Inc Device 2100
    Flags: bus master, fast devsel, latency 0, IRQ 75, NUMA node 0, IOMMU group 15
    Memory at fce00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: nvme
    Kernel modules: nvme

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 25, IOMMU group 16
    I/O ports at e000 [size=256]
    Memory at fcd04000 (64-bit, non-prefetchable) [size=4K]
    Memory at fcd00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

04:00.0 Network controller: MEDIATEK Corp. Device 0616
    Subsystem: Foxconn International, Inc. Device e0df
    Flags: bus master, fast devsel, latency 0, IRQ 97, IOMMU group 17
    Memory at fca00000 (64-bit, prefetchable) [size=1M]
    Memory at fcb00000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: mt7921e
    Kernel modules: mt7921e

05:00.0 PCI bridge: ASMedia Technology Inc. Device 242a (rev 01) (prog-if 00 [Normal decode])
    Physical Slot: 0-1
    Flags: bus master, fast devsel, latency 0, IRQ 24, IOMMU group 18
    Bus: primary=05, secondary=06, subordinate=07, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: fc600000-fc9fffff [size=4M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

06:02.0 PCI bridge: ASMedia Technology Inc. Device 242b (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 25, IOMMU group 19
    Bus: primary=06, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: [disabled]
    Memory behind bridge: fc600000-fc9fffff [size=4M]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: <access denied>
    Kernel driver in use: pcieport

07:00.0 USB controller: ASMedia Technology Inc. Device 242c (rev 01) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 20af
    Flags: bus master, fast devsel, latency 0, IRQ 25, IOMMU group 19
    Memory at fc600000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci

08:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 164e (rev d8) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 226d
    Flags: bus master, fast devsel, latency 0, IRQ 57, IOMMU group 20
    Memory at fc10000000 (64-bit, prefetchable) [size=256M]
    Memory at fc20000000 (64-bit, prefetchable) [size=2M]
    I/O ports at d000 [size=256]
    Memory at fc500000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu

08:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] VanGogh PSP/CCP
    Subsystem: ASUSTeK Computer Inc. VanGogh PSP/CCP
    Flags: bus master, fast devsel, latency 0, IRQ 94, IOMMU group 21
    Memory at fc400000 (32-bit, non-prefetchable) [size=1M]
    Memory at fc5c8000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ccp
    Kernel modules: ccp

08:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15b6 (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 20af
    Flags: bus master, fast devsel, latency 0, IRQ 48, IOMMU group 22
    Memory at fc300000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci

08:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15b7 (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 20af
    Flags: bus master, fast devsel, latency 0, IRQ 57, IOMMU group 23
    Memory at fc200000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci

08:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor (rev 62)
    Subsystem: ASUSTeK Computer Inc. Raven/Raven2/FireFlight/Renoir Audio Processor
    Flags: bus master, fast devsel, latency 0, IRQ 98, IOMMU group 24
    Memory at fc580000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: snd_rpl_pci_acp6x
    Kernel modules: snd_pci_acp3x, snd_rn_pci_acp3x, snd_pci_acp5x, snd_pci_acp6x, snd_acp_pci, snd_rpl_pci_acp6x, snd_pci_ps, snd_sof_amd_renoir, snd_sof_amd_rembrandt

08:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
    DeviceName: Realtek ALC1220
    Subsystem: ASUSTeK Computer Inc. Family 17h (Models 10h-1fh) HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 100, IOMMU group 25
    Memory at fc5c0000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

09:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15b8 (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. Device 20af
    Flags: bus master, fast devsel, latency 0, IRQ 24, IOMMU group 26
    Memory at fcc00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci



Any idea on how to fix this?

Thank you in advance.
Best,
Dedalus

---

