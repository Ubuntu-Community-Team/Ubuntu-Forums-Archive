---
title: "Logitech G502 mouse frozen for 1 minute at boot after 15.10 upgrade"
date: 2015-12-08
forum: Hardware
---

### Post by sye737 on 2015-12-08
I recently upgraded to 15.10 and my G502 mouse now is frozen in the center of the screen on boot for about a minute, which did not happen before. The relevant dmesg logs as far as I can see:

```

[    2.552193] usb 1-10: new full-speed USB device number 4 using xhci_hcd[    2.681490] usb 1-10: New USB device found, idVendor=046d, idProduct=c07d
[    2.681493] usb 1-10: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.681494] usb 1-10: Product: Gaming Mouse G502
[    2.681494] usb 1-10: Manufacturer: Logitech
[    2.681495] usb 1-10: SerialNumber: 0C68344C3736
[    2.848623] usb 1-11: new full-speed USB device number 5 using xhci_hcd

```

and then much later...

```

[   85.129858] input: Logitech Gaming Mouse G502 as /devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.0/0003:046D:C07D.0006/input/input22
[   85.184769] hid-generic 0003:046D:C07D.0006: input,hidraw3: USB HID v1.11 Mouse [Logitech Gaming Mouse G502] on usb-0000:00:14.0-10/input0
[   85.185500] input: Logitech Gaming Mouse G502 as /devices/pci0000:00/0000:00:14.0/usb1/1-10/1-10:1.1/0003:046D:C07D.0007/input/input23
[   85.240838] hid-generic 0003:046D:C07D.0007: input,hiddev0,hidraw4: USB HID v1.11 Keyboard [Logitech Gaming Mouse G502] on usb-0000:00:14.0-10/input1

```

---

