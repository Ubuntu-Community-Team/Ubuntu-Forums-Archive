---
title: "USB Serial FTDI Adapter"
date: 2011-05-16
forum: Hardware
---

### Post by yesinndeedy on 2011-05-16
I installed Ubuntu 11.04 on a CR-48 and trying to use a USB serial adapter (FTDI). I can't seem to get access to the device. Here is some output from dmesg | grep -i USB

[    2.885067] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    3.064275] usb 4-2: New USB device found, idVendor=0403, idProduct=6001
[    3.064287] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.064296] usb 4-2: Product: usb serial converter
[    3.064303] usb 4-2: Manufacturer: FTDI
[    3.064309] usb 4-2: SerialNumber: FTCYH5DD
[    3.064554] usb 4-2: configuration #1 chosen from 1 choice
[    3.279173] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    3.368616] USB Serial support registered for Qualcomm USB modem
[    3.368679] qcserial 1-2:1.1: Qualcomm USB modem converter detected
[    3.369248] usb 1-2: Qualcomm USB modem converter now attached to ttyUSB0
[    3.369549] usbcore: registered new interface driver qcserial

I expecting it to connect to /dev/ttyUSB1 or something. Is there something else that would make this work?
Thanks

---

