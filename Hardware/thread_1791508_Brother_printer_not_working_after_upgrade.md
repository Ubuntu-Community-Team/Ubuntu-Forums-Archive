---
title: "Brother printer not working after upgrade"
date: 2011-06-26
forum: Hardware
---

### Post by plizzba on 2011-06-26
I've recently upgraded my computers to 11.04, and now my Brother DCP-7020 printer fails to work on all three of my computers, which are running ubuntu.

The printer doesn't show up when I run "lsusb." After plugging the printer into the usb port I see the following output from "dmesg"

```
[  250.624030] usb 7-1: new full speed USB device using uhci_hcd and address 2
[  250.744031] usb 7-1: device descriptor read/64, error -71
[  250.968027] usb 7-1: device descriptor read/64, error -71
[  251.184050] usb 7-1: new full speed USB device using uhci_hcd and address 3
[  251.304020] usb 7-1: device descriptor read/64, error -71
[  251.528041] usb 7-1: device descriptor read/64, error -71
[  251.744039] usb 7-1: new full speed USB device using uhci_hcd and address 4
[  252.152083] usb 7-1: device not accepting address 4, error -71
[  252.264033] usb 7-1: new full speed USB device using uhci_hcd and address 5
[  252.672032] usb 7-1: device not accepting address 5, error -71
[  252.672047] hub 7-0:1.0: unable to enumerate USB device on port 1
[  255.028035] usb 7-1: new full speed USB device using uhci_hcd and address 6
...

```I've tried all kinds of things without any luck. Any ideas? Thank you for your help.

---

### Post by plizzba on 2011-06-27
Found the problem: Our cat had chewed holes in the usb cable! :mad:

---

