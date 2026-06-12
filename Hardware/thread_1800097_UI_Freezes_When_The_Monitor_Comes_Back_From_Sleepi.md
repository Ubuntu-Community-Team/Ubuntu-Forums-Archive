---
title: "UI Freezes When The Monitor Comes Back From Sleeping"
date: 2011-07-08
forum: Hardware
---

### Post by thomasca on 2011-07-08
Hi, I have a Lenovo IdeaCentre K320 desktop with Natty Narwhal Ubuntu installed on it, and every time I have the monitor sleep and come back to it after a while, the entire UI (besides the mouse) would completely freeze.

I disabled the screen saver to see if that was the issue, and it wasn't. I would even freeze the screen saver if that was enabled.

---

### Post by thomasca on 2011-07-08
This is what I get for the lspci for this system:


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18 )
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18 )
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)

---

### Post by thomasca on 2011-07-12
It seems that telling ubuntu not to put the monitor to sleep fixes this issue.

---

