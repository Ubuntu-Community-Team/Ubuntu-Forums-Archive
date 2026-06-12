---
title: "USB hub - Pilot Sync"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by rscottroberts on 2005-08-29
My computer will not recognize some of my devices when plugged into a USB hub. They work fine when plugged directly into the computer.

I have a Targus mini 4-port hub. Keyboard and mouse work fine, but printer and Pilot sync do not.

Devices plugged into hub look like this:
:~$ lsusb
Bus 004 Device 003: ID 0518:0001 EzKEY Corp.
Bus 004 Device 002: ID 05e3:0605 Genesys Logic, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Devices plugged into computer look like this:
:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0557:2006 ATEN International Co., Ltd UC-1284B Printer Port
Bus 001 Device 003: ID 0518:0001 EzKEY Corp.
Bus 001 Device 001: 082d:0300 Handspring Treo 600

Any help with USB hub issue is appreciated.

---

