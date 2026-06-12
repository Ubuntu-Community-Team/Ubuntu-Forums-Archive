---
title: "Usb port not working.  &quot;device descriptor read/64, error -71&quot;"
date: 2011-11-04
forum: Hardware
---

### Post by Chikitulfo on 2011-11-04
Hi, 

Since this morning the logitech usb mouse that I usually use with the laptop is not working.

This is the content of /var/log/syslog
```
tail -30 /var/log/syslog
Nov  4 12:16:37 tetto kernel: [ 1431.640079] usb 7-1: new low speed USB device using uhci_hcd and address 115
Nov  4 12:16:37 tetto kernel: [ 1431.770088] usb 7-1: device descriptor read/64, error -71
Nov  4 12:16:38 tetto kernel: [ 1432.010222] usb 7-1: device descriptor read/64, error -71
Nov  4 12:16:38 tetto kernel: [ 1432.240065] usb 7-1: new low speed USB device using uhci_hcd and address 116
Nov  4 12:16:38 tetto kernel: [ 1432.660097] usb 7-1: device not accepting address 116, error -71
Nov  4 12:16:38 tetto kernel: [ 1432.780079] usb 7-1: new low speed USB device using uhci_hcd and address 117
Nov  4 12:16:39 tetto kernel: [ 1433.200045] usb 7-1: device not accepting address 117, error -71
Nov  4 12:16:39 tetto kernel: [ 1433.200082] hub 7-0:1.0: unable to enumerate USB device on port 1
Nov  4 12:16:41 tetto kernel: [ 1435.010091] usb 7-1: new low speed USB device using uhci_hcd and address 118
Nov  4 12:16:41 tetto kernel: [ 1435.140085] usb 7-1: device descriptor read/64, error -71
Nov  4 12:16:41 tetto kernel: [ 1435.380076] usb 7-1: device descriptor read/64, error -71
Nov  4 12:16:41 tetto kernel: [ 1435.610081] usb 7-1: new low speed USB device using uhci_hcd and address 119
Nov  4 12:16:41 tetto kernel: [ 1435.740119] usb 7-1: device descriptor read/64, error -71
Nov  4 12:16:42 tetto kernel: [ 1435.980044] usb 7-1: device descriptor read/64, error -71
Nov  4 12:16:42 tetto kernel: [ 1436.210151] usb 7-1: new low speed USB device using uhci_hcd and address 120
Nov  4 12:16:42 tetto kernel: [ 1436.630061] usb 7-1: device not accepting address 120, error -71
Nov  4 12:16:42 tetto kernel: [ 1436.750073] usb 7-1: new low speed USB device using uhci_hcd and address 121
Nov  4 12:16:43 tetto kernel: [ 1437.170046] usb 7-1: device not accepting address 121, error -71
Nov  4 12:16:43 tetto kernel: [ 1437.170083] hub 7-0:1.0: unable to enumerate USB device on port 1
Nov  4 12:16:45 tetto kernel: [ 1438.980091] usb 7-1: new low speed USB device using uhci_hcd and address 122
Nov  4 12:16:45 tetto kernel: [ 1439.110085] usb 7-1: device descriptor read/64, error -71
Nov  4 12:16:45 tetto kernel: [ 1439.350075] usb 7-1: device descriptor read/64, error -71
Nov  4 12:16:45 tetto kernel: [ 1439.580060] usb 7-1: new low speed USB device using uhci_hcd and address 123
Nov  4 12:16:45 tetto kernel: [ 1439.710083] usb 7-1: device descriptor read/64, error -71
Nov  4 12:16:46 tetto kernel: [ 1439.950108] usb 7-1: device descriptor read/64, error -71
Nov  4 12:16:46 tetto kernel: [ 1440.180082] usb 7-1: new low speed USB device using uhci_hcd and address 124
Nov  4 12:16:46 tetto kernel: [ 1440.600072] usb 7-1: device not accepting address 124, error -71
Nov  4 12:16:46 tetto kernel: [ 1440.720102] usb 7-1: new low speed USB device using uhci_hcd and address 125
Nov  4 12:16:47 tetto kernel: [ 1441.140052] usb 7-1: device not accepting address 125, error -71
Nov  4 12:16:47 tetto kernel: [ 1441.140090] hub 7-0:1.0: unable to enumerate USB device on port 1

```

The mouse is working correctly because if I plug it in a different usb port it gets recogniced and it works.
```
hub 7-0:1.0: unable to enumerate USB device on port 1
Nov  4 12:26:31 tetto kernel: [ 2024.840064] usb 7-1: new low speed USB device using uhci_hcd and address 84
Nov  4 12:26:31 tetto kernel: [ 2024.970115] usb 7-1: device descriptor read/64, error -71
Nov  4 12:26:31 tetto kernel: [ 2025.210026] usb 7-1: device descriptor read/64, error -71
Nov  4 12:26:31 tetto kernel: [ 2025.440072] usb 7-1: new low speed USB device using uhci_hcd and address 85
Nov  4 12:26:31 tetto kernel: [ 2025.570089] usb 7-1: device descriptor read/64, error -71
Nov  4 12:26:32 tetto kernel: [ 2025.810123] usb 7-1: device descriptor read/64, error -71
Nov  4 12:26:32 tetto kernel: [ 2025.980123] hub 7-0:1.0: unable to enumerate USB device on port 1
Nov  4 12:26:37 tetto kernel: [ 2031.360084] usb 6-1: new low speed USB device using uhci_hcd and address 2
Nov  4 12:26:37 tetto kernel: [ 2031.650934] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input10
Nov  4 12:26:37 tetto kernel: [ 2031.651505] generic-usb 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1/input0
Nov  4 12:26:37 tetto kernel: [ 2031.653127] usbcore: registered new interface driver usbhid
Nov  4 12:26:37 tetto kernel: [ 2031.653134] usbhid: USB HID core driver

```

I also tried with a couple of pendrives that I have here, and the result is the same, they work properly in one port and they don't in the other one.

I'm not sure whether it is a software or hardware problem in that usb port, so any help is appreciated.

I guess it is a hardware one, but I want to be sure before I start to replace the usb port physically

EDIT: Using ubuntu 11.04 arch:amd64 kernel:2.6.38-12-generic

---

