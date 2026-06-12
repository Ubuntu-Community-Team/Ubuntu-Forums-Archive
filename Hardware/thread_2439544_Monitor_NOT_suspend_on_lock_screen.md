---
title: "Monitor NOT suspend on lock screen"
date: 2020-03-29
forum: Hardware
---

### Post by Josh_Hill on 2020-03-29
Good day everyone.  This issue has been plaguing me since 18.04 (now on 19.10).  <insert obligatory newbie/light Ubuntu experience excuses>

I've been unable to get my three screens to go into standby (power off) while at the lock screen.  Current timeouts are set for 5 minutes via settings.

What i've tried (after searching/googling/general cursing) so far is to play with xset.

What I've noticed:
1. @Lock screen, no change to monitors @ 5 minute (which is what I have my defaults set to) mark.

2. DPMS is enabled w/ standby set to 0.  However, after executing 'xset dpms 5', DPMS standby does show a change.  Screens go blank (for a bit) then blink on/off a few times.  Re-querying xset shows Standby has changed.

What I fear is that there is some program (vague recollection of a gnome extension which isn't installed anymore) causing the mouse to move slightly to bring the screens out of standby.

Please help me identify what is going on and how to get the monitors to go into standby when the screen is locked.  Any advice/help is greatly appreciated.

Monitors (there are 3 of the exact same model):
```

~$ sudo get-edid | parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 5
No EDID on bus 6
No EDID on bus 7
No EDID on bus 10
4 potential busses found: 0 4 8 9
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
Bus 0 doesn't really have an EDID...
256-byte EDID successfully retrieved from i2c bus 4
Looks like i2c was successful. Have a good day.
Checksum Correct


Section "Monitor"
    Identifier "G276HL"
    ModelName "G276HL"
    VendorName "ACR"
    # Monitor Manufactured week 15 of 2015
    # EDID version 1.3
    # Digital Display
    DisplaySize 600 340
    Gamma 2.20
    Option "DPMS" "true"
    Horizsync 31-83
    VertRefresh 56-76
    # Maximum pixel clock is 170MHz
    #Not giving standard mode: 1152x864, 75Hz
    #Not giving standard mode: 1280x960, 60Hz
    #Not giving standard mode: 1280x1024, 60Hz
    #Not giving standard mode: 1280x720, 60Hz
    #Not giving standard mode: 1280x800, 60Hz
    #Not giving standard mode: 1440x900, 60Hz
    #Not giving standard mode: 1680x1050, 60Hz
    #Not giving standard mode: 1920x1080, 60Hz


    #Extension block found. Parsing...
    Modeline     "Mode 16" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 0" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 1" 25.200 640 656 752 800 480 490 492 525 -hsync -vsync
    Modeline     "Mode 2" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 3" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 4" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
    Modeline     "Mode 5" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
    Modeline     "Mode 6" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
    Modeline     "Mode 7" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
    Modeline     "Mode 8" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 9" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
    Modeline     "Mode 10" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
    Modeline     "Mode 11" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
    Modeline     "Mode 12" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
    Modeline     "Mode 13" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
    Modeline     "Mode 14" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
    Modeline     "Mode 15" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 17" 74.25 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
    Modeline     "Mode 18" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync 
    Modeline     "Mode 19" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync 
    Option "PreferredMode" "Mode 16"
EndSection

```

Environment:
```

~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) I/O Memory Management Unit
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe GPP Bridge
00:01.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe GPP Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe GPP Bridge
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
00:07.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
00:07.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Internal PCIe GPP Bridge 0 to Bus B
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 59)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Data Fabric: Device 18h; Function 7
01:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM961/PM961
02:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset USB 3.1 xHCI Controller (rev 02)
02:00.1 SATA controller: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset SATA Controller (rev 02)
02:00.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 43b2 (rev 02)
03:00.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
03:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
03:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
03:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
03:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
03:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] 300 Series Chipset PCIe Port (rev 02)
05:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter (rev 03)
08:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
0a:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] (rev e7)
0a:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]
0b:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Zeppelin/Raven/Raven2 PCIe Dummy Function
0b:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) Platform Security Processor
0b:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) USB 3.0 Host Controller
0c:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Zeppelin/Renoir PCIe Dummy Function
0c:00.2 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 51)
0c:00.3 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) HD Audio Controller

```


current xset -q results:

```

~$ xset -q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  33
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```

---

