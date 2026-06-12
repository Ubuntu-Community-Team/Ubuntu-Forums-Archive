---
title: "usb stick sometimes unknown"
date: 2008-11-05
forum: Hardware
---

### Post by jackm on 2008-11-05
Hi all,
sometimes usb-stick isn't knowen by my system, the dmesg's output is :
```
[ 1823.847969] usb 5-3: new high speed USB device using ehci_hcd and address 17
[ 1822.396260] usb 5-3: configuration #1 chosen from 1 choice
[ 1822.396710] scsi16 : SCSI emulation for USB Mass Storage devices
[ 1822.397223] usb-storage: device found at 17
[ 1822.397228] usb-storage: waiting for device to settle before scanning
[ 1823.244572] usb-storage: device scan complete
[ 1824.835564] scsi 16:0:0:0: Direct-Access     USB 2.0  Flash Disk       0.00 PQ: 0 ANSI: 2
[ 1824.837623] sd 16:0:0:0: [sdb] 1024000 512-byte hardware sectors (524 MB)
[ 1853.253377] usb 5-3: reset high speed USB device using ehci_hcd and address 17
[ 1883.395055] usb 5-3: reset high speed USB device using ehci_hcd and address 17
[ 1913.581691] usb 5-3: reset high speed USB device using ehci_hcd and address 17
[ 1943.729167] usb 5-3: reset high speed USB device using ehci_hcd and address 17
[ 1973.869665] usb 5-3: reset high speed USB device using ehci_hcd and address 17
[ 2004.055399] usb 5-3: reset high speed USB device using ehci_hcd and address 17
[ 2004.188244] sd 16:0:0:0: [sdb] Write Protect is off
[ 2004.188255] sd 16:0:0:0: [sdb] Mode Sense: 55 53 42 53
[ 2004.188260] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[ 2005.778729] sd 16:0:0:0: [sdb] 1024000 512-byte hardware sectors (524 MB)
[ 2034.202637] usb 5-3: reset high speed USB device using ehci_hcd and address 17
[ 2064.388692] usb 5-3: reset high speed USB device using ehci_hcd and address 17
```
any help ?
thnax

---

### Post by boof1988 on 2008-11-20
Bump

---

