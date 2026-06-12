---
title: "Second monitor blank (ATI radeon driver)"
date: 2012-05-11
forum: Hardware
---

### Post by nfarley88 on 2012-05-11
I recently plugged in a second monitor to my ubuntu 12.04 installation, and it correctly recognises there is a monitor attached, and even assigns a valid resolution to it, but the monitor remains blank (i.e. no signal to the monitor).

My lspci is 
```


00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6530D]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:15.2 PCI bridge: Advanced Micro Devices [AMD] Device 43a2
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller

```

and my xrandr output is 
```

VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0 +   75.1*    70.1  
   800x600        75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
HDMI-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 16mm x 9mm
   1920x1080i     30.0 +
   1280x720       60.0  
   1024x768       75.1     70.1     60.0* 
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x480        59.9  
   640x480        72.8     75.0     66.7     60.0 

```

My HDMI-0 is my primary output.

Thanks for the help!

---

