---
title: "Scanjet 4470c problems"
date: 2008-11-21
forum: Hardware
---

### Post by broxtor on 2008-11-21
I'm trying to get my scanjet 4470c scanner to work in Kubuntu 8.04, This scanner wasn't supported by sane for a long time, but the sane compatability list now says it is supported by means of the rts8891 backend. In the Kubuntu repositories this backend is in the package libsane-extras and I have installed this.

Kubuntu now recognizes the scanner, but when I try to scan the applications crash. Kooka crashes right after I selected my scanner in the scanner selection window. When I try scanimage from a terminal it crashes with a segmentation fault.
Does anyone know how I can make this work?

Some output:
```

broxtor@ghost:~$ lsusb
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 03f0:0805 Hewlett-Packard
Bus 001 Device 005: ID 044f:b107 ThrustMaster, Inc.
Bus 001 Device 004: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 001 Device 002: ID 03f0:1104 Hewlett-Packard DeskJet 959c
Bus 001 Device 001: ID 0000:0000

sane-find-scanner:
found USB scanner (vendor=0x03f0, product=0x0805, chip=rts8801/rts8891) at libusb:001:006

broxtor@ghost:~$ scanimage -L
device `hp_rts88xx:libusb:001:006' is a Hewlett-Packard ScanJet 4470C flatbed scanner

```

---

