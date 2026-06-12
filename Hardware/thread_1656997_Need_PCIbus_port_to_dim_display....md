---
title: "Need PCIbus port to dim display..."
date: 2010-12-31
forum: Hardware
---

### Post by popcornman on 2010-12-31
Hello all!
I'm running Lucid on a Toshiba A665D-S6059 Laptop, and Ubuntu doesn't seem to want to change my screen brightness when I edit it in the Power Management. I read on a post [_here_]("http://www1.ubuntuforums.org/showthread.php?p=9562142") that you can set a script with setpci and ACPI to dim the brightness when on battery. Well the problem is I have never dealt with PCIbus ports so I am quite clueless about which one to select. 
I compiled a list of the PCIbus ports with lspci while in single user and hopefully someone can give me a hand with selecting the correct port. Thank you all in advance.:popcorn:
> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:03.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 1)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
09:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
09:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
09:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
09:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
0a:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

---

