---
title: "Blank screen on external monitor out of VGA1: intel"
date: 2014-10-31
forum: Hardware
---

### Post by kos4 on 2014-10-31
Hello,
I am working on an Acer Travelmate and I have upgraded to xubuntu 14.10 hoping that it would have sorted out an issue that I have got the last few days with my VGA1.. But I do not see that  happening.
Here is my issue... 
Everything was working fine when I had my two external monitors plugged in to VGA and DVI. Xubuntu was able to detect both of them and I have been able to work with both of them with no problems for few weeks. 
One morning though the monitor which is plugged in to VGA1  has decided to go blank which  means that the monitor,even though it shows that has got the power and  display something, returns a black screen. Running xrandar I cannot see any problem as I can detect the monitor as usual. I can detect the monitor even with  the 'display' GUI and therefore no problem there either..


This is the detail about my graphics card. 
```
Graphics:  Card: Intel Mobile 915GM/GMS/910GML Express Graphics Controller
           Display Server: X.Org 1.16.0 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1280x1024@60.0hz, 1280x1024@60.0hz
           GLX Renderer: Mesa DRI Intel 915GM x86/MMX/SSE2
           GLX Version: 1.4 Mesa 10.3.0
```

This is my xrandar...
```

Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 32767 x 32767
LVDS1 connected (normal left inverted right x axis y axis)
   1024x768       60.0 +
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1280x960       60.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     60.0  
   720x400        70.1  
DVI1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 359mm x 287mm
   1280x1024      60.0*+
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
TV1 unknown connection (normal left inverted right x axis y axis)
   848x480        59.9 +
   640x480        59.9 +
   1024x768       59.9  
   800x600        59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

and finally, here is my kernel usage...
```
 ~$ lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: i915
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 007a
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
    Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: snd_intel8x0
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 007a
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: lpc_ich
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
    Subsystem: Acer Incorporated [ALI] Device 007a
05:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: firewire_ohci
05:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 005e
    Kernel driver in use: tg3
05:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
    Subsystem: Intel Corporation WM3B2300BG Mini-PCI Card
    Kernel driver in use: ipw2200
05:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: yenta_cardbus
05:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 007a
05:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: sdhci-pci
05:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 007a
05:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 007a
    Kernel driver in use: sdhci-pci
```



 is it because my graphics cards has been corrupted? How someone can check that?


Any help so that I get my second monitor to be alive again will be appreciated..

Thanks!

---

