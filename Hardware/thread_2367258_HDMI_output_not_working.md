---
title: "HDMI output not working"
date: 2017-07-28
forum: Hardware
---

### Post by ekinskofer on 2017-07-28
Hey all,

I'm trying to give an old laptop new life by making it the kids media player. It's an older HP DV7 and I'm running Lubuntu 17.04. 

```

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

```
 
I've tried to get the HDMI to work to no avail. I've tested the tv with another laptop and the HDMI works fine with that. This laptop also outputs to a 24" monitor via HDMI no problem. When I have the laptop plugged in the laptop lcd screen resolution is also outside of the viewing area and I can't figure out where to change the resolution. Here's the xrandr --current with the laptop plugged in. 

```

xrandr --current
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
LVDS-1 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1600x900      60.08*+
   1440x900      59.89  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080     60.00*+  59.94    24.00    23.98  
   1920x1080i    60.00    59.94  
   1400x1050     59.95  
   1280x1024     60.02  
   1280x720      60.00    59.94  
   1024x768      60.00  
   1440x480i     59.94  
   800x600       60.32  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       60.00    59.94  
DP-1 disconnected (normal left inverted right x axis y axis)

```

I also can't seem to figure out how to make the screen external/mirrored/etc. The regular fn+f4 doesn't appear to be working. Any help would be AWESOME. 

additional info:

lspci
```

lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation HM55 Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)

```

thanks so much.

cheers.
Eric

---

### Post by ekinskofer on 2017-07-29
Bump. Any ideas? Links? Additional info needed? Thanks in advance.

---

