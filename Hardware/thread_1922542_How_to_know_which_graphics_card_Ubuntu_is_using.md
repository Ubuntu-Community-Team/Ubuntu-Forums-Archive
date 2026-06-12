---
title: "How to know which graphics card Ubuntu is using?"
date: 2012-02-09
forum: Hardware
---

### Post by madeoforanges on 2012-02-09
Hello,

I'm completely NEW to Ubuntu.

I have a MSI 970-G45 and it has a built-in Radeon GPU. I tried disabling the Radeon GPU in the BIOs, but BIOs doesn't have an option to do so. I have the Nvidia GeForce Ti 550 installed on my motherboard, but I don't know which GPU is Ubuntu using. In addition, I installed the 'NVIDA accelerated graphics driver' by activating it from the 'additional drivers' menu in 'system settings'. I don't know what else I can do from here.

> 
madeoforanges@madeoforanges:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port B)
00:09.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port H)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
**01:00.0 VGA compatible controller: nVidia Corporation GF116 [GeForce GTX 550 Ti] (rev a1)**
01:00.1 Audio device: nVidia Corporation Device 0bee (rev a1)
02:00.0 USB Controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)


I only want to play Starcraft 2.

-oranges :)

---

