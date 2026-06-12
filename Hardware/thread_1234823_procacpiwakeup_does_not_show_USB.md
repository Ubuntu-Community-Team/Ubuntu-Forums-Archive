---
title: "/proc/acpi/wakeup does not show USB"
date: 2009-08-08
forum: Hardware
---

### Post by ruben0 on 2009-08-08
I want to be able to turn my laptop on from suspend with my remote control. In order to do so I know I have to enable this in the wakeup. 

The problem I'm having is the USB devices are not shown in the list.

It's BUS002 Device003, but as you can see in wakeup it's not shown. Anyone knows how I should enable this?

mediacenter@mediacenter:~$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless
Transceiver (ACPI-compliant)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mediacenter@mediacenter:~$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
LID0      S3    *enabled
PWRB      S4    *enabled
AZAL      S4     disabled  pci:0000:00:1b.0
RP01      S3     disabled  pci:0000:00:1c.0
PXS1      S3     disabled  pci:0000:02:00.0
LANC      S4     disabled
MODM      S4     disabled
mediacenter@mediacenter:~$

---

