---
title: "Unable to detect the USB serial RS232"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by techie_india on 2009-03-13
Hi all ,

Im using RS232 usb-serial converter .

When I plugin to my machine it is giving the following error 

```
[ 3625.660021] usb 4-1: new full speed USB device using uhci_hcd and address 7
[ 3625.809048] usb 4-1: device descriptor read/all, error -84
[ 3625.920032] usb 4-1: new full speed USB device using uhci_hcd and address 8
[ 3626.068051] usb 4-1: device descriptor read/all, error -84
[ 3626.184015] usb 4-1: new full speed USB device using uhci_hcd and address 9
[ 3626.229047] usb 4-1: device descriptor read/all, error -32
[ 3626.340025] usb 4-1: new full speed USB device using uhci_hcd and address 10
[ 3626.387048] usb 4-1: unable to read config index 0 descriptor/all
[ 3626.387056] usb 4-1: can't read configurations, error -84
[ 3626.389049] hub 4-0:1.0: unable to enumerate USB device on port 1
[ 4129.648034] usb 4-1: new full speed USB device using uhci_hcd and address 11
[ 4129.776028] usb 4-1: device descriptor read/64, error -84
[ 4130.043052] usb 4-1: unable to read config index 0 descriptor/all
[ 4130.043064] usb 4-1: can't read configurations, error -84
[ 4130.156023] usb 4-1: new full speed USB device using uhci_hcd and address 12
[ 4130.360033] usb 4-1: device descriptor read/all, error -84
[ 4130.472021] usb 4-1: new full speed USB device using uhci_hcd and address 13
[ 4130.510054] usb 4-1: device descriptor read/all, error -84
[ 4130.680040] usb 4-1: new full speed USB device using uhci_hcd and address 14
[ 4130.780658] usb 4-1: configuration #1 chosen from 1 choice
[ 4130.784061] usb 4-1: can't set config #1, error -32
[ 4195.336065] usb 4-1: USB disconnect, address 14
[ 4440.916533] usb 4-1: new full speed USB device using uhci_hcd and address 15
[ 4441.078645] usb 4-1: configuration #1 chosen from 1 choice
[ 4441.178054] usbcore: registered new interface driver usbserial
[ 4441.178076] usbserial: USB Serial support registered for generic
[ 4441.178114] usbcore: registered new interface driver usbserial_generic
[ 4441.178116] usbserial: USB Serial Driver core
[ 4441.181222] usbserial: USB Serial support registered for pl2303
[ 4441.181260] pl2303 4-1:1.0: pl2303 converter detected
[ 4441.193238] usb 4-1: pl2303 converter now attached to ttyUSB0
[ 4441.193265] usbcore: registered new interface driver pl2303
[ 4441.193268] pl2303: Prolific PL2303 USB to serial adaptor driver
[ 4486.488057] usb 4-1: USB disconnect, address 15
[ 4486.489933] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[ 4486.491317] pl2303 4-1:1.0: device disconnected

```

Can anybody help how to detect the RS232 interface

Im using Ubuntu 8.1

Thanks and regards
Anshuman Srivastava

---

