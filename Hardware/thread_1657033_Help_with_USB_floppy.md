---
title: "Help with USB floppy"
date: 2010-12-31
forum: Hardware
---

### Post by rvaughnmd on 2010-12-31
Trying to get a BYTECC BT-144 usb external floppy working in Ubuntu. Label states this is a TEAC FD-05PUB. Drivers included are for Mac and Windows can't find any Linux references at either site, in the document or CD that came with the device. 

rich@Sparky09:~$ dmesg | tail
[ 9625.412065] usb 5-2: device descriptor read/64, error -62
[ 9625.656061] usb 5-2: device descriptor read/64, error -62
[ 9625.896063] usb 5-2: new full speed USB device using ohci_hcd and address 4
[ 9626.037546] usb 5-2: device descriptor read/64, error -62
[ 9626.281059] usb 5-2: device descriptor read/64, error -62
[ 9626.520068] usb 5-2: new full speed USB device using ohci_hcd and address 5
[ 9626.929548] usb 5-2: device not accepting address 5, error -62
[ 9627.064054] usb 5-2: new full speed USB device using ohci_hcd and address 6
[ 9627.472316] usb 5-2: device not accepting address 6, error -62
[ 9627.472341] hub 5-0:1.0: unable to enumerate USB device on port 2
rich@Sparky09:~$

No mention of the device with lsusb:

rich@Sparky09:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 04f9:0016 Brother Industries, Ltd Printer
Bus 003 Device 003: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
rich@Sparky09:~$ 

Any hope with this device or is it irrevocably, fatally incompatible with Linux?

---

