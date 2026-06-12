---
title: "Onboard graphics card not detected"
date: 2011-08-19
forum: Hardware
---

### Post by nathanhillinbl on 2011-08-19
I have an ECS A790GXM-AD3 motherboard, which has a ATI Radeon HD 3300 onboard, as well as an ATI Radeon HD 4870 in a PCIe slot. The 3300 isn't detected whatsoever (lspci, lshw), and the 4870 is. I would like to be able to use both simultaneously. 

I'm currently running Ubuntu 11.04 64bit. 

Here's my lspci output

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:03.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02)
nate@NattyButNotCrappyBeer:~$ 

``` 

If anyone can be of assistance, it would be greatly appreciated.

Thanks,
Nate

---

### Post by coffeecat on 2011-08-19
This is a BIOS issue. Most BIOSs automatically disable the onboard graphics when you fit a PCIe graphics card. Hence it is not seen with lspci, etc. However, you should be able to enable both graphics devices in the BIOS. I have an ECS motherboard (different model) with an American Megatrends BIOS. The settings for graphics are under PCI/PnP Settings. On my BIOS there are two parameters to set - the first for one or both graphics devices, the second for priority.

If your BIOS is not American Megatrends, you'll have to search for where the settings are.

---

