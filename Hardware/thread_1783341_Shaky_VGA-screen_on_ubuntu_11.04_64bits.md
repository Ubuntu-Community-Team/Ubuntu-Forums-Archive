---
title: "Shaky VGA-screen on ubuntu 11.04 64bits"
date: 2011-06-15
forum: Hardware
---

### Post by danielwc on 2011-06-15
Hi,

I am trying to connect an external LCD monitor on my ubuntu 11.04, but this external monitor is flickering. I've tested with Windows and works fine, then, is not a hardware problem.

My notebook has no HDMI port, then must use the VGA port. Can someone help me?

lspci:
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18 )
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18 )
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

---

### Post by eudennis on 2011-07-05
I'm with the exactly same problem. Did you got any advance on that?

I made one script that help, but doesn't work everytime, you could try:

```

#!/bin/bash
sleep 15
xrandr --output VGA1 --mode 1280x768 --rate 60

```

---

### Post by CMOS4081 on 2011-07-05
Try using the native resolution of the external monitor.
Set the refresh rate as mention in a previous reply to what the display supports. Try the auto set feature most monitors have.
Good Luck! :D

---

