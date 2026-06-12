---
title: "How do I install video card driver...."
date: 2008-05-01
forum: Hardware
---

### Post by Cjames on 2008-05-01
for a IBM Laptop T23 using a S3 SuperSavage/IXC. I tried the "Applications/Other/Screens and Graphics" control and it will let me set my monitor as Generic LCD Panel 1024-768 but keeps crashing when I try to set the card. right now I'm using "vesa-Generic VESA-complaint video cards" Do I need to reinstall Hardy 8.04 or go back to 7.10? 

This is a clean install. Dual-boot with WinXP.


lspci:
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

 dmesg | grep agp
[   16.390016] Linux agpgart interface v0.102
[   16.440902] agpgart: Detected an Intel 830M Chipset.
[   16.565847] agpgart: AGP aperture is 256M @ 0xd0000000


Anyone using a T23 that can help me out?

---

