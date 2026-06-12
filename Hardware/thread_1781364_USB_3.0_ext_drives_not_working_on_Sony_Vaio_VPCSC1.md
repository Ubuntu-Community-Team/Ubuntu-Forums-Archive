---
title: "USB 3.0 ext drives not working on Sony Vaio VPCSC1AFM/S"
date: 2011-06-13
forum: Hardware
---

### Post by CLTPilot on 2011-06-13
This is the "Blue Label" Sony VAIO from BestBuy.  It's setup as dual boot Win7/Ubuntu 11.04.

  It has a single USB 3.0 port and 2 USB 2.0 ports.  I've bought a Western Digital USB 3.0 2TB external drive and a Seagate USB 3.0 3TB external drive.  Neither shows up when plugged into the USB 3 port.  The Seagate will show up when plugged into a 4 port USB 2.0 hub but the WD will not.    I also connected a USB 2 FreeAgent Go 750GB drive to the USB 3 port and it shows up ok.  So the port is working, but not for the 2 USB 3 drives I have

The WD 3.0 drive works fine in Win7, I did not check the other 3.0 drive yet.  Here's the output from the lsusb command:

Bus 003 Device 002: ID 0bc2:2101 Seagate RSS LLC 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 008: ID 0bc2:50a1 Seagate RSS LLC 
Bus 002 Device 006: ID 04f9:01e9 Brother Industries, Ltd 
Bus 002 Device 005: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:64b5 Microdia 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Any ideas on how to fix this?   

Thanks

---

