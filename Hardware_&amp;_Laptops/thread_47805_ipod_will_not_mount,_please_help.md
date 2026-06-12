---
title: "ipod will not mount, please help"
date: 2005-07-10
forum: Hardware &amp; Laptops
---

### Post by shortcircuit on 2005-07-10
an 4th gen ipod mini w/ usb connection

i plug it in and get this error from dmesg:

```
scsi104 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 17
usb-storage: waiting for device to settle before scanning
usb 4-5: USB disconnect, address 17
usb 4-5: new high speed USB device using ehci_hcd and address 18
usb 4-5: can't set config #1, error -71
usb 4-5: new high speed USB device using ehci_hcd and address 19
usb 4-5: device not accepting address 19, error -71
``` 

then the ipod says "ok to disconnect"

-sam

---

### Post by andlinux21 on 2005-07-10
you got these errors from gtk-pod?

---

### Post by shortcircuit on 2005-07-10
these errors came from the dmesg command after plugging the ipod into my computer via usb

---

### Post by shortcircuit on 2005-07-10
this is really weird

i have a usb 256m thumb drive witch automounts fine in ubuntu, and the ipod will mount but only if the thumbdrive is alredy mounted

if the usb disk is not mounted the ipod will not mount

when i plug the ipod in by itself i get this sring of errors from the dmesg command:

```
scsi115 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 90
usb-storage: waiting for device to settle before scanning
usb 4-5: USB disconnect, address 90
usb 4-5: new high speed USB device using ehci_hcd and address 91
scsi116 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 91
usb-storage: waiting for device to settle before scanning
usb 4-5: USB disconnect, address 91
usb 4-5: new high speed USB device using ehci_hcd and address 92
scsi117 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 92
usb-storage: waiting for device to settle before scanning
usb 4-5: USB disconnect, address 92
usb 4-5: new high speed USB device using ehci_hcd and address 93
usb 4-5: can't set config #1, error -71
usb 4-5: new high speed USB device using ehci_hcd and address 94
scsi118 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 94
usb-storage: waiting for device to settle before scanning
usb 4-5: USB disconnect, address 94
usb 4-5: new high speed USB device using ehci_hcd and address 95
usb 4-5: can't set config #1, error -71
usb 4-5: new high speed USB device using ehci_hcd and address 96
usb 4-5: can't set config #1, error -71
usb 4-5: new high speed USB device using ehci_hcd and address 97
usb 4-5: new high speed USB device using ehci_hcd and address 98
scsi119 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 98
usb-storage: waiting for device to settle before scanning
usb 4-5: USB disconnect, address 98
usb 4-5: new high speed USB device using ehci_hcd and address 99
scsi120 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 99
usb-storage: waiting for device to settle before scanning
usb 4-5: USB disconnect, address 99
usb 4-5: new high speed USB device using ehci_hcd and address 100
usb 4-5: device descriptor read/64, error -71
usb 4-5: can't set config #1, error -71
usb 4-5: new high speed USB device using ehci_hcd and address 101
scsi121 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 101
usb-storage: waiting for device to settle before scanning
usb 4-5: USB disconnect, address 101
usb 4-5: new high speed USB device using ehci_hcd and address 102
scsi122 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 102
usb-storage: waiting for device to settle before scanning
usb 4-5: USB disconnect, address 102
usb 4-5: new high speed USB device using ehci_hcd and address 103
scsi123 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 103
usb-storage: waiting for device to settle before scanning
usb 4-5: USB disconnect, address 103
usb 4-5: new high speed USB device using ehci_hcd and address 104
scsi124 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 104
usb-storage: waiting for device to settle before scanning
usb 4-5: USB disconnect, address 104
usb 4-5: new high speed USB device using ehci_hcd and address 105
usb 4-5: device not accepting address 105, error -71
usb 4-5: new high speed USB device using ehci_hcd and address 106
usb 4-5: new high speed USB device using ehci_hcd and address 107
usb 4-5: device not accepting address 107, error -71
usb 4-5: new high speed USB device using ehci_hcd and address 108
usb 4-5: can't set config #1, error -71
shortcircuit@ubuntu:~$
```

---

### Post by shortcircuit on 2005-07-10
found the solution to my own problem, its a power issue, the usb ports on the back of my pc have enough power to run the ipod, i was using the ones on the front witch do not

---

