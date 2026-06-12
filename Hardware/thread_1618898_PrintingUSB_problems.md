---
title: "Printing/USB problems"
date: 2010-11-11
forum: Hardware
---

### Post by Ideaus on 2010-11-11
-Printer(hp) works with Windows
-Printer is initially recognized
-Connection to printer is suddenly lost
-lsusb can nolonger find the printer
-dmesg outputs:
[ 8370.795237] usblp0: removed
[ 8492.160120] usb 7-1: reset full speed USB device using uhci_hcd and address 3
[ 8507.280048] usb 7-1: device descriptor read/64, error -110
[ 8522.510111] usb 7-1: device descriptor read/64, error -110
[ 8522.740053] usb 7-1: reset full speed USB device using uhci_hcd and address 3
[ 8537.860271] usb 7-1: device descriptor read/64, error -110
[ 8553.090051] usb 7-1: device descriptor read/64, error -110
[ 8553.322566] usb 7-1: reset full speed USB device using uhci_hcd and address 3
[ 8558.341980] usb 7-1: device descriptor read/8, error -110
[ 8563.471990] usb 7-1: device descriptor read/8, error -110
[ 8563.700143] usb 7-1: reset full speed USB device using uhci_hcd and address 3
[ 8568.721985] usb 7-1: device descriptor read/8, error -110
[ 8573.851983] usb 7-1: device descriptor read/8, error -110
[ 8573.960099] usb 7-1: USB disconnect, address 3
[ 8573.960136] sd 4:0:0:0: Device offlined - not ready after error recovery
[ 8574.102583] usb 7-1: new full speed USB device using uhci_hcd and address 4
[ 8574.230036] usb 7-1: device descriptor read/64, error -71
[ 8574.472534] usb 7-1: device descriptor read/64, error -71
[ 8574.700144] usb 7-1: new full speed USB device using uhci_hcd and address 5
[ 8574.830158] usb 7-1: device descriptor read/64, error -71
[ 8575.080109] usb 7-1: device descriptor read/64, error -71
[ 8575.310116] usb 7-1: new full speed USB device using uhci_hcd and address 6
[ 8575.730132] usb 7-1: device not accepting address 6, error -71
[ 8575.850141] usb 7-1: new full speed USB device using uhci_hcd and address 7
[ 8576.270125] usb 7-1: device not accepting address 7, error -71
[ 8576.270148] hub 7-0:1.0: unable to enumerate USB device on port 1
[ 8866.350147] usb 7-1: new full speed USB device using uhci_hcd and address 8
[ 8866.480156] usb 7-1: device descriptor read/64, error -71
[ 8866.720120] usb 7-1: device descriptor read/64, error -71
[ 8866.950127] usb 7-1: new full speed USB device using uhci_hcd and address 9
[ 8867.080136] usb 7-1: device descriptor read/64, error -71
[ 8867.320119] usb 7-1: device descriptor read/64, error -71
[ 8867.550115] usb 7-1: new full speed USB device using uhci_hcd and address 10
[ 8867.970141] usb 7-1: device not accepting address 10, error -71
[ 8868.090152] usb 7-1: new full speed USB device using uhci_hcd and address 11
[ 8868.510152] usb 7-1: device not accepting address 11, error -71
[ 8868.510183] hub 7-0:1.0: unable to enumerate USB device on port 1

---

### Post by dino99 on 2010-11-11
[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

