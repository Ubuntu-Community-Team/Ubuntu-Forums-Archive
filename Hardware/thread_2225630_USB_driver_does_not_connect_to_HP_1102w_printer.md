---
title: "USB driver does not connect to HP 1102w printer"
date: 2014-05-22
forum: Hardware
---

### Post by lsiden on 2014-05-22
I have a HP 1102w USB/wifi printer.  When I connect it to any USB port (USB2 or USB3), it fails to connect.  So the hp-setup utility cannot complete the setup.  Here are the syslog messages that get posted when I plug it in

May 22 09:36:17 morpheus kernel: [219709.178739] usb 3-9: new full-speed USB device number 35 using xhci_hcd
May 22 09:36:17 morpheus kernel: [219709.178897] usb 3-9: Device not responding to set address.
May 22 09:36:17 morpheus kernel: [219709.382751] usb 3-9: Device not responding to set address.
May 22 09:36:18 morpheus kernel: [219709.586552] usb 3-9: device not accepting address 35, error -71
May 22 09:36:18 morpheus kernel: [219709.698585] usb 3-9: new full-speed USB device number 36 using xhci_hcd
May 22 09:36:18 morpheus kernel: [219709.698741] usb 3-9: Device not responding to set address.
May 22 09:36:18 morpheus kernel: [219709.902629] usb 3-9: Device not responding to set address.
May 22 09:36:18 morpheus kernel: [219710.106370] usb 3-9: device not accepting address 36, error -71
May 22 09:36:18 morpheus kernel: [219710.218396] usb 3-9: new full-speed USB device number 37 using xhci_hcd
May 22 09:36:18 morpheus kernel: [219710.218518] usb 3-9: Device not responding to set address.
May 22 09:36:18 morpheus kernel: [219710.422405] usb 3-9: Device not responding to set address.
May 22 09:36:19 morpheus kernel: [219710.626217] usb 3-9: device not accepting address 37, error -71
May 22 09:36:19 morpheus kernel: [219710.738281] usb 3-9: new full-speed USB device number 38 using xhci_hcd
May 22 09:36:19 morpheus kernel: [219710.738453] usb 3-9: Device not responding to set address.
May 22 09:36:19 morpheus kernel: [219710.942321] usb 3-9: Device not responding to set address.
May 22 09:36:19 morpheus kernel: [219711.146101] usb 3-9: device not accepting address 38, error -71
May 22 09:36:19 morpheus kernel: [219711.146198] hub 3-0:1.0: unable to enumerate USB device on port 9

Is this a USB issue or an HP issue?

Linux morpheus 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 010: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 009: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 003 Device 003: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 003 Device 002: ID 04a9:1907 Canon, Inc. CanoScan LiDE 700F
Bus 003 Device 008: ID 8087:07da Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

