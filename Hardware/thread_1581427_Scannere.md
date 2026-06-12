---
title: "Scannere"
date: 2010-09-24
forum: Hardware
---

### Post by satimis on 2010-09-24
Hi folks,

Ubuntu 10.04 64-bit
Epson scanner Perfection 3490 Photo
XSane Image Scanner

Applications -> XSane Image Scanner
Warning```

Failed to open device snapscan:libuse:001:015 invalid argument

```

$ lsusb```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:071f Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 016: ID 04b8:0122 Seiko Epson Corp. Perfection 3590 scanner
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
It is there.

$ scanimage -L```

device `snapscan:libusb:001:016' is a EPSON EPSON Scanner flatbed scanner

```

It is there as well


I found following thread;
[ubuntu] How to get Epson 3490 Scanner working under Hardy H
[http://wwww.ubuntuforums.org/showthread.php?p=9387348](http://wwww.ubuntuforums.org/showthread.php?p=9387348)

but it is for Hardy,

Please advise.  TIA

B.R.
satimis

---

