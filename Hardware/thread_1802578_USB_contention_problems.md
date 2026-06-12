---
title: "USB contention problems"
date: 2011-07-12
forum: Hardware
---

### Post by john00 on 2011-07-12
Running 11.04 64-bit

I've had some USB problems with a new ASRock H61M/U3S3 motherboard. It has 2 USB2 controllers and 1 USB3 controller.  They all work fine when there is only one device attached to each controller, but once my USB headset or webcam tries to share a controller with something else, there are problems. 

When the USB headset is plugged in the same controller as the mouse, as soon as audio is output to it, the mouse cursor stops moving, and starts again when the audio stops.

When connecting the webcam at the same time as the mouse (or anything else), in the same USB2 bus it doesn't work, and reports 
libv4l2: error turning on stream: No space left on device 

The devices can happily coexist on the USB3 controller

In addition to that, probably a separate issue, when I plug in my PCI DVB tuner card, then the USB3 controller isn't recognised, and I get the error logged:
USB Controller: Device 1b21:1042 Unknown header type 7f



Any ideas on where to start with these?

$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation 6 Series Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series Chipset Family 2 port SATA IDE Controller (rev 05)
02:00.0 PCI bridge: Device 1b21:1080 (rev 01)
04:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
05:00.0 USB Controller: Device 1b21:1042
06:00.0 IDE interface: Device 1b21:0611 (rev 01)


$ lsusb
Bus 003 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 002 Device 004: ID 047f:da40 Plantronics, Inc. 
Bus 002 Device 003: ID 056a:0014 Wacom Co., Ltd Graphire 3 6x8
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

