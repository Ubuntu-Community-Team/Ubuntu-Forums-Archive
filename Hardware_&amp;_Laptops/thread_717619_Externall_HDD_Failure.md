---
title: "Externall HDD Failure"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by Edible_Monkey on 2008-03-07
Ive got an external hdd that simply refuses to mount. Heres a quick system log to have a gander at:
> Mar  7 13:37:55 ubuntu-laptop kernel: [95910.632000] usb 1-1: new full speed USB device using uhci_hcd and address 18
Mar  7 13:37:56 ubuntu-laptop kernel: [95910.796000] usb 1-1: configuration #1 chosen from 1 choice
Mar  7 13:37:56 ubuntu-laptop kernel: [95910.800000] scsi23 : SCSI emulation for USB Mass Storage devices
Mar  7 13:37:56 ubuntu-laptop kernel: [95910.800000] usb-storage: device found at 18
Mar  7 13:37:56 ubuntu-laptop kernel: [95910.800000] usb-storage: waiting for device to settle before scanning
Mar  7 13:38:01 ubuntu-laptop kernel: [95915.800000] usb-storage: device scan complete
Mar  7 13:38:06 ubuntu-laptop kernel: [95921.412000] usb 1-1: reset full speed USB device using uhci_hcd and address 18
Mar  7 13:38:16 ubuntu-laptop kernel: [95931.664000] usb 1-1: reset full speed USB device using uhci_hcd and address 18
Mar  7 13:38:22 ubuntu-laptop kernel: [95936.916000] usb 1-1: reset full speed USB device using uhci_hcd and address 18
Mar  7 13:38:32 ubuntu-laptop kernel: [95947.176000] usb 1-1: reset full speed USB device using uhci_hcd and address 18
Mar  7 13:38:32 ubuntu-laptop kernel: [95947.320000] scsi 23:0:0:0: scsi: Device offlined - not ready after error recovery

Im not overly sure whats going on here, im basically trying to recover the data from the hdd but havent previously had this issue. Does anyone have any ideas on how to mount this hdd ?

---

### Post by teaker1s on 2008-03-12
try knoppix bootable iso. it will allow mounting of damaged hdd.

---

