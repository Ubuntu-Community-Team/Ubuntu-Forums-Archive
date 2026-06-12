---
title: "USB Serial Adapter issues"
date: 2016-10-17
forum: Hardware
---

### Post by jerryz2013 on 2016-10-17
My setup Ubuntu 16.04 LTS
uname -a returns:
4.4.0-43-generic #63-Ubuntu SMP Wed Oct 12 13:48:03 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
 
I have a USB serial adapter that used to work, however lately has some issues. Here is the output of dmesg:

[96170.084431] usb 2-1.2: new full-speed USB device number 5 using ehci-pci
[96170.181535] usb 2-1.2: unable to read config index 0 descriptor/start: -32
[96170.181543] usb 2-1.2: chopping to 0 config(s)
[96170.183883] usb 2-1.2: string descriptor 0 read error: -32
[96170.183890] usb 2-1.2: New USB device found, idVendor=067b, idProduct=2303
[96170.183894] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[96170.184130] usb 2-1.2: no configuration chosen from 0 choices

The strange this is that the scripts seems unable to resolve critical information about this device and yet when I run lsusb I get the following information:

Bus 002 Device 008: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

This behaviour started I believe, after I connected a different USB serial port adapter that even now seems to work ok, here is the dmesg of that adapter being inserted:

[98614.812498] usb 2-1.2: Manufacturer: FTDI
[98614.812502] usb 2-1.2: SerialNumber: A800eymj
[98614.846575] usbcore: registered new interface driver usbserial
[98614.846599] usbcore: registered new interface driver usbserial_generic
[98614.846618] usbserial: USB Serial support registered for generic
[98614.852148] usbcore: registered new interface driver ftdi_sio
[98614.852223] usbserial: USB Serial support registered for FTDI USB Serial Device
[98614.852349] ftdi_sio 2-1.2:1.0: FTDI USB Serial Device converter detected
[98614.852405] usb 2-1.2: Detected FT232RL
[98614.852721] usb 2-1.2: FTDI USB Serial Device converter now attached to ttyUSB0

Any help soving this puzzle would be appreciated, Thanks!

---

