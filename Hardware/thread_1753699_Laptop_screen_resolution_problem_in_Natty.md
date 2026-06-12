---
title: "Laptop screen resolution problem in Natty"
date: 2011-05-09
forum: Hardware
---

### Post by Humppis on 2011-05-09
Hey folks,

recently updated to ubuntu 11.04. My laptop, Acer Aspire 1360, has major problems with screen resolution though: in the previous version I could use the 1024x768 resolution without a problem but now the system only allows a 800x600 resolution max. 

So says xrandr:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   720x576        60.0  
   800x480        60.0  
   720x480        60.0  
   640x480        60.0  

```

So says lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Ethernet controller: InProComm Inc. IPN 2220 802.11g
00:0b.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
00:0b.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
00:0b.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

```

Here's something I suspect to be relevant from the xorg.0.log:
```
[  5534.580] (II) CHROME(0): ViaSecondCRTCModeValid
[  5534.580] (II) CHROME(0): Not using default mode "1024x768" (exceeds panel dimensions)
[
```


I noticed at first boot a brief error message concerning resolution, so I guess the new resolution detector is broken? Now I've a 800x600 picture on the screen on the high left-hand corner, and another picture seems to begin under it! I've plummaged the internet for answers but to no avail. Please assist.

---

### Post by Humppis on 2011-05-10
I've tried also simply setting up new resolutions for the default output in xrandr with the help of cvt or gtf as per the x.org wiki:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

What happens:

```
jonttu@jonttu-laptop:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   720x576        60.0  
   800x480        60.0  
   720x480        60.0  
   640x480        60.0  
jonttu@jonttu-laptop:~$ cvt 1024 768 60
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
jonttu@jonttu-laptop:~$ xrandr --newmode "cvt"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default
jonttu@jonttu-laptop:~$ xrandr --addmode default cvt
xrandr: Failed to get size of gamma for output default
jonttu@jonttu-laptop:~$ xrandr --output default --mode cvt
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed

```

I also tried to make a virtual 1024x768 desktop, but interestingly, now that 1024x768 virtual desktop is stuffed into the 800x600 display! Hopefully someone would come up with some ideas so this thread won't remain as a mere monolog!

---

### Post by abelta on 2011-05-27
I'm having exactly the same problem and with Natty as well after formatting and reinstalling. No solution so far and I've tried everything.

---

