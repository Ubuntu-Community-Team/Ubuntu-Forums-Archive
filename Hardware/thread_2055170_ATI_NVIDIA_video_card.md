---
title: "ATI NVIDIA video card"
date: 2012-09-08
forum: Hardware
---

### Post by warday27 on 2012-09-08
On my machine I have a dedicated video card gforce 9500gt and an integrated ATI 4000 series.
If i'm not wrong ATI is disabled. But from what I saw in the new kernel, from 3.5 the 2 video cards could run simultaneously.
It is possible to have two different video cards running in kubuntu 12.4?  or In the next version of kubuntu12.10  can?
Is this true?
That's my question, thanks for all!

---

### Post by Xanthius on 2012-09-08
Please do "sudo lshw" or "lspci" so we have a better view of your hardware.

Such as Optimus is a technology of nVidia to switch between internal and descrete GPU, this could be true for you as well.

Sadly, that technology is still badly supported in Linux. But there is work in progress, bumblebee / ironhide and even nVidia themselves as I've read.

---

### Post by warday27 on 2012-09-08
I used lspci Because the other was too mach long
Motherboard: product: GA-880GM-USB3 ()  vendor: Gigabyte Technology Co., Ltd.
Processor Phenom 2 965 3.4gh

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9500 GT] (rev a1)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

Thanks for your answer. One think that I would like to know if there is possible that both of the graphic cards can work together.(I know that its relay difficult because they have different architecture but I think that on open software nothing is impossible)XD

---

