---
title: "Dual-Monitors HP Envy"
date: 2011-03-18
forum: Hardware
---

### Post by linuxuse on 2011-03-18
I just installed Ubuntu. I can't get the ATI drivers working, but I'm not sure if I need them or not. I want to do Dual-Monitors on my HP Envy with an ATI Radeon 5650. I have a Mini-DVI to DVI and an HDMI to DVI adapters. When I click "Detect Monitors" neither will display. I know that my cables and monitors are working because it works under Windows.

Please let me know if you have any suggestions.

Thank you.

Here is my lspci output:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

---

### Post by linuxuse on 2011-03-18
A few more things to note.

When I run xrandr -q, I get:

Screen 0: minimum 320 x 200, current 1360 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 321mm x 181mm
   1366x768       59.6 +
   1360x768       59.8*    60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  

When I plugin my mini-dvi cable I get moving fuzz. When I plugin my HDMI to DVI cable, I get fixed static.

---

### Post by linuxuse on 2011-03-20
Bump. Help would be greatly appreciated.

---

