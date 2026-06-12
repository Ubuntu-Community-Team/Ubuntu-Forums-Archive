---
title: "Touchpad issues"
date: 2014-06-21
forum: Hardware
---

### Post by judderwocky on 2014-06-21
So here is what happens. I can toggle the touchpad on my Toshiba C55-A5100 using the FN + F5 button  It normally works fine, except occassionally (at really incovenient times) it doesn't turn the touchpad back on.   Ive only been able to reproduce this bug sometimes... and it only occurs under the following circumstances.   First I disable the touchpad   Then I remove the mouse.   When I try to toggle the touchpad back on, this is the message.     >     kernel: [  197.194213] psmouse serio1: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.   kernel: [  207.674390] usb 3-3: new low-speed USB device number 3 using xhci_hcd   kernel: [  207.806620] usb 3-3: New USB device found, idVendor=045e, idProduct=0040   kernel: [  207.806623] usb 3-3: New USB device strings: Mfr=1, Product=3, SerialNumber=0   kernel: [  207.806625] usb 3-3: Product: Microsoft 3-Button Mouse with IntelliEye(TM)  kernel: [  207.806627] usb 3-3: Manufacturer: Microsoft  kernel: [  207.806774] usb 3-3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes   kernel: [  207.808940] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/0003:045E:0040.0002/input/input12  kernel: [  207.809310] hid-generic 0003:045E:0040.0002: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:14.0-3/input0  As soon as I restart everything is fine. 

---

