---
title: "USB Problems"
date: 2009-05-14
forum: Hardware
---

### Post by zyxyellowxyz on 2009-05-14
It seems as if every once-in-a-blue-moon my USB mouse and keyboard will decide they don't want to work. The other day, it was both; today, just the mouse.
(Before I get into it any further: My keyboard hooks up to the computer via USB, there is a USB port on the keyboard itself, which I have a 4-port USB hub plugged in so that my wireless mouse's sensor can be closer to the mouse than if I had it plugged into the tower. The hub is also used for my webcam, printer, and my SD card adapter when I need them. At the moment, the aforementioned are not connected to the hub. There are 2 USB ports on the back side of the tower (both used by the keyboard), an internally USB connected card read on the front of the tower with 2 USB ports, and the previously mentioned 4 port USB hub plugged into the USB port on the keyboard.)

Because I honestly don't know why I'm having these problems, I decided to show the following:

lsusb:
```
Bus 001 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 003 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 002: ID 1532:0109 Razer USA, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

dmesg |grep usb
```
[    0.552414] usbcore: registered new interface driver usbfs
[    0.552414] usbcore: registered new interface driver hub
[    0.552414] usbcore: registered new device driver usb
[    2.828154] usb usb1: configuration #1 chosen from 1 choice
[    2.828574] usb usb2: configuration #1 chosen from 1 choice
[    2.828870] usb usb3: configuration #1 chosen from 1 choice
[    2.829174] usb usb4: configuration #1 chosen from 1 choice
[    2.829480] usb usb5: configuration #1 chosen from 1 choice
[    2.829655] usbcore: registered new interface driver libusual
[    2.829695] usbcore: registered new interface driver usbserial
[    2.829727] usbcore: registered new interface driver usbserial_generic
[    2.829729] usbserial: USB Serial Driver core
[    3.364524] usb 1-7: new high speed USB device using ehci_hcd and address 4
[    3.515161] usb 1-7: configuration #1 chosen from 1 choice
[    3.524692] usbcore: registered new interface driver usb-storage
[    3.524802] usb-storage: device found at 4
[    3.524804] usb-storage: waiting for device to settle before scanning
[    3.756045] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    3.928976] usb 3-1: configuration #1 chosen from 1 choice
[    4.172047] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    4.341988] usb 3-2: configuration #1 chosen from 1 choice
[    4.629905] usb 3-2.4: new low speed USB device using uhci_hcd and address 4
[    4.770004] usb 3-2.4: configuration #1 chosen from 1 choice
[    8.524724] usb-storage: device scan complete
[    9.699845] usbcore: registered new interface driver hiddev
[    9.703429] input: Razer Razer Lycosa as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[    9.716371] generic-usb 0003:1532:0109.0001: input,hidraw0: USB HID v1.10 Keyboard [Razer Razer Lycosa] on usb-0000:00:1d.1-1/input0
[    9.725232] input: Razer Razer Lycosa as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input4
[    9.738581] generic-usb 0003:1532:0109.0002: input,hidraw1: USB HID v1.10 Device [Razer Razer Lycosa] on usb-0000:00:1d.1-1/input1
[    9.753505] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.4/3-2.4:1.0/input/input5
[    9.756215] generic-usb 0003:046D:C521.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2.4/input0
[    9.784349] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.4/3-2.4:1.1/input/input6
[    9.792401] generic-usb 0003:046D:C521.0004: input,hiddev96,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2.4/input1
[    9.792430] usbcore: registered new interface driver usbhid
[    9.792457] usbhid: v2.6:USB HID core driver
```

Yes, my mouse battery is good. I'm not getting any kind of error message that it doesn't have enough power (in fact, I never get that message that the battery is dying). I think it has to do with the USB connections themselves because, as I mentioned above, my keyboard stopped working the other day and only a forced shutdown/reboot seemed to fix it (I pressed and held down the power button). This is becoming an annoying re-occurring experience that I hope can be solved.

---

