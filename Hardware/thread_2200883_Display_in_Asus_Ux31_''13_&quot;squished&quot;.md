---
title: "Display in Asus Ux31 ''13 &quot;squished&quot;"
date: 2014-01-21
forum: Hardware
---

### Post by zeke3 on 2014-01-21
I recently installed Ubuntu 13.10 and, although virtually every driver works perfectly, my screen seems to "squish" almost all programs. It's just enough to make the experience stressful. I've looked everywhere but still no solution to the problem. The worst part is that the external monitor is also showing this behavior which leads me to believe that it's not a driver issue but something in the config of the OS.


Here's some debug info:

lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation QS67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
03:00.0 USB controller: Fresco Logic FL1009 USB 3.0 Host Controller (rev 02)

---

