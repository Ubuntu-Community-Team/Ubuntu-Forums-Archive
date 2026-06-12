---
title: "Media Card Reader Will Not Mount"
date: 2008-06-18
forum: Hardware
---

### Post by omagdon7 on 2008-06-18
Hi I'm using an HP Pavilion ze2000, I've installed Hardy Heron and I cannot get my media card reader, which is built-in, to mount my xD card.  The reader does however show up when I run lspci in a terminal.  The output is below, I haven't been able to figure it out and would really appreciate some direction.

> 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller


This is the output of dmesg | tail -n 20.

> [  344.324638] tifm_core: SmartMedia/xD card detected in socket 0:2
[  404.084148] tifm0 : demand removing card from socket 0:2
[  407.357499] tifm_core: SmartMedia/xD card detected in socket 0:2


---

### Post by omagdon7 on 2008-06-23
bump

---

### Post by blueturtl on 2008-06-25
Chiming in with my Compaq nx6125 and similar problem.

Hardware is detected but seems to not be operating.

```
lspci | grep Texas:

02:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

```

Would be interested in seeing a solution.

---

### Post by blueturtl on 2008-06-26
omagdon7,

I may have found the solution to our problem, albeit my [source]("http://ubuntulinuxtipstricks.blogspot.com/2007/04/texas-instruments-sdmmc-card-reader.html") says it might be risky.

The solution is to enter the command
```
setpci -s 05:09.3 4c=0x22
```
into a terminal. The reader should then work.

This command is supposed to change some register value in the card reader.
The identifier of the device needs to match your own, and that has been provided by your 'lspci' output:
> 
**05:09.3** Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

Try at your own risk! I have tried the command, but I don't have a memory card to test it with.

---

