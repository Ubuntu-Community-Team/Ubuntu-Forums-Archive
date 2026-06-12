---
title: "&quot;reset low-speed usb device number using xhci_hcd&quot; on official HP Dock"
date: 2020-09-27
forum: Hardware
---

### Post by christian79 on 2020-09-27
Hello,

I have installed Ubuntu 20.04 on my EliteBook 830 G6. I have an HP Thunderbolt Dock 120 W G2 which has a power supply and is connected via usb c to my notebook. I only had my mouse, keyboard and a usb microphone connected on it, but they kept losing connection.
I checked dmesg and found lots of messages:
```

[  +0,052791] usb 5-1.3.7: new full-speed USB device number 10 using xhci_hcd
[  +2,943835] retire_capture_urb: 380 callbacks suppressed
[  +0,516726] usb 5-1.3.2: reset full-speed USB device number 7 using xhci_hcd
[  +0,543820] usb 5-1.3.1: reset low-speed USB device number 6 using xhci_hcd
[  +0,604112] usb 5-1.3.1: reset low-speed USB device number 6 using xhci_hcd
[  +0,375959] usb 5-1.3.2: reset full-speed USB device number 7 using xhci_hcd
[  +0,275489] usb 5-1.3.7: New USB device found, idVendor=03f0, idProduct=0667, bcdDevice= 1.00
[  +0,000006] usb 5-1.3.7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  +0,000004] usb 5-1.3.7: Product: WinUSB
[  +0,000004] usb 5-1.3.7: Manufacturer: Cypress Semiconductor
[  +0,000003] usb 5-1.3.7: SerialNumber: 1.0
[  +0,020442] hid-generic 0003:03F0:0667.0038: hiddev2,hidraw8: USB HID v1.11 Device [Cypress Semiconductor WinUSB] on usb-0000:06:00.0-1.3.7/input1
[  +1,444019] usb 5-1.3.2: reset full-speed USB device number 7 using xhci_hcd
[  +1,407431] retire_capture_urb: 32 callbacks suppressed
[  +0,264486] usb 5-1.3.2: reset full-speed USB device number 7 using xhci_hcd
[  +1,248041] usb 5-1.3.2: reset full-speed USB device number 7 using xhci_hcd
[  +1,248102] usb 5-1.3.2: reset full-speed USB device number 7 using xhci_hcd

```
(The full log after I plugged in the dock: [https://paste.ubuntu.com/p/9Mbn6dxkYD/](https://paste.ubuntu.com/p/9Mbn6dxkYD/))

This keeps on and on and the mouse and keyboard keep disconnecting over and over again. I already found in a German Ubuntu forum to add ```
options usbcore autosuspend=-1
``` to [FONT=courier new]/etc/modprobe.d/usb-core-options[/FONT] and restart. It did not work.
Currently I am using a cheap usb c hub which has some usb type a ports. They work without any issue.

Do you have any idea how to fix this issue?

Best regards,
christian

---

