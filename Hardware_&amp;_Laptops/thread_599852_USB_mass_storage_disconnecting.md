---
title: "USB mass storage disconnecting?"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by mcarro on 2007-11-01
I am experiencing disconnections from USB mass storage devices (an USB stick and two USB freecom hard disks).  These used to work without problems under Feisty, but they get disconnected under Gutsy with no apparent reason (and a message appears on my desktop tellling me to be careful).

Removing and inserting them again does not help: they are not recognized (fdisk -l does not show a trace of them). /var/log/messages shows, after pluging in the usb disk again, messages like the ones below


Nov  1 17:04:33 balboa kernel: [60907.012000] usb 4-4: new high speed USB device using ehci_hcd and address 127
Nov  1 17:04:37 balboa kernel: [60910.696000] usb 4-4: new high speed USB device using ehci_hcd and address 20
Nov  1 17:04:39 balboa kernel: [60913.064000] usb 4-4: new high speed USB device using ehci_hcd and address 32
Nov  1 17:04:40 balboa kernel: [60914.492000] usb 4-4: new high speed USB device using ehci_hcd and address 39
Nov  1 17:04:44 balboa kernel: [60918.364000] usb 4-4: new high speed USB device using ehci_hcd and address 59
Nov  1 17:04:49 balboa kernel: [60922.660000] usb 4-4: new high speed USB device using ehci_hcd and address 78
Nov  1 17:04:49 balboa kernel: [60923.336000] usb 4-4: new high speed USB device using ehci_hcd and address 81
Nov  1 17:04:50 balboa kernel: [60924.200000] usb 4-4: new high speed USB device using ehci_hcd and address 85
Nov  1 17:04:53 balboa kernel: [60927.508000] usb 4-4: new high speed USB device using ehci_hcd and address 102
Nov  1 17:04:54 balboa kernel: [60927.996000] usb 4-4: new high speed USB device using ehci_hcd and address 104


Any idea of what could be going on, or which additional information would be needed to find out the problem?  Thanks a lot!

---

