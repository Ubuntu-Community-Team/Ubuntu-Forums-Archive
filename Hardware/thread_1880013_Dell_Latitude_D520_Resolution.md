---
title: "Dell Latitude D520 Resolution"
date: 2011-11-12
forum: Hardware
---

### Post by dwessell on 2011-11-12
Hi,

I have a Dell Latitude D520 that I can't get to go about 1024x768. There aren't other options. But I know that it's capable because it has higher options in Windows. Can someone point me in the right direction?

Here's my lspci:


dwessell@dwessell-Latitude-D520:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by dwessell on 2011-11-13
My xorg log file shows:

[PHP]
[125563.848] (II) intel(0): Printing DDC gathered Modelines:
[125563.848] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync$
[/PHP]
I ran through the xrandr process that is documented in the wiki and it adds the mode, but doesn't assign it to LVDS1.

[PHP]
dwessell@dwessell-Latitude-D520:/var/log$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)
  1280x1024_60.00 (0x5eb)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
  1280x1024-60.00 (0x652)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
  1280x1024+60.00 (0x66a)  108.9MHz
        h: width  1280 start 1360 end 1496 total 1712 skew    0 clock   63.6KHz
        v: height 1024 start 1025 end 1028 total 1060           clock   60.0Hz
[/PHP]
If I try and add the mode it fails:

[PHP]dwessell@dwessell-Latitude-D520:/var/log$ sudo xrandr --addmode LVDS1 "1280x1024+60.00"
[sudo] password for dwessell: 
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30
[/PHP]

So as far as I can tell I need to either tell something to ignore the edid information reported, or make a manual xorg.conf entry. Is that correct? Is there good documentation that I'm not finding for this?

Thanks
David

---

### Post by MoreOrLess on 2011-11-13
AFAICT, unless you got the d520 with the premium screen (which supports 1400x1050), then 1024x768 IS the native resolution. [http://www.notebookreview.com/default.asp?newsID=3150](http://www.notebookreview.com/default.asp?newsID=3150)

---

