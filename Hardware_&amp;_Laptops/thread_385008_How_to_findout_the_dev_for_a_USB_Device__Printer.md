---
title: "How to findout the dev for a USB Device / Printer"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by RetSam on 2007-03-15
I connect my Printer to my USB port, (Cannon MPC400) but I don't get the /dev/ulpx device.

When running lsusb the Driver is visible: (btw. Mouse, and External Drive works fine)
#lssub
Bus 004 Device 004: ID 0d49:5020 Maxtor
Bus 004 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c024 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 04a9:2611 Canon, Inc. SmartBase MPC400
Bus 001 Device 001: ID 0000:0000

I would now expect a /dev/ulp* something but:
#ls /dev/u*
/dev/urandom

Who does normally generate the ulp? in dev? The Kernel ? Is there a configuration file? Probably the config cannot decide if this is a printer or scanner because it is both.
Any ideas what went wrong?

btw. I use ubuntu 6.10
# uname -a
Linux aceru 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

---

