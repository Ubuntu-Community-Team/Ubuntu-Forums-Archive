---
title: "dmesg - constant USB new device"
date: 2016-12-09
forum: Hardware
---

### Post by ian-board on 2016-12-09
I have a USB issue that is annoying (14.04 on ThinkPad W520)

If I look at the dmesg, I get this:

[ 1756.032947] usb 1-1.3: new full-speed USB device number 44 using ehci-pci
[ 1756.801087] usb 1-1.3: new full-speed USB device number 46 using ehci-pci
[ 1757.569208] usb 1-1.3: new full-speed USB device number 48 using ehci-pci
[ 1758.337361] usb 1-1.3: new full-speed USB device number 50 using ehci-pci
[ 1759.105484] usb 1-1.3: new full-speed USB device number 52 using ehci-pci
[ 1759.873604] usb 1-1.3: new full-speed USB device number 54 using ehci-pci
[ 1760.641734] usb 1-1.3: new full-speed USB device number 56 using ehci-pci
[ 1761.409892] usb 1-1.3: new full-speed USB device number 58 using ehci-pci
 
Which goes on forever. Normally, I would lean towards hardware problem, but everything just seems to work fine regardless of speed (can mix usb 2.0, 3.0 no problems). I have seem similar things listed in forums, but usually in the context of usb resets, refusing to enumerate, etc.  - there is none of that here, just the 'new device' messages.

Listing usb devices gives:

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1058:0748 Western Digital Technologies, Inc. My Passport (WDBKXH, WDBY8L)
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 04f2:b217 Chicony Electronics Co., Ltd Lenovo Integrated Camera (0.3MP)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I tried a live CD of 16.04 and the problem is still there.

Anyone have any thoughts on this?  It seems harmless but it is very irritating.

---

