---
title: "How to setup USB to RS232 adapter as standard com port"
date: 2010-05-29
forum: Hardware
---

### Post by lotech on 2010-05-29
I've a Windows s/w for logging data from an electronic equipment connect via RS232 port, since my netbook has no serial port I use an USB to RS232 adapter instead, the s/w is written for Win95 and can run under Wine, my question is how to setup the device so that it will replace standard serial port ? The s/w does not support other than the 4 standard serial ports on the PC, here is some detail of it :

[  497.757745] usb 1-1.4: configuration #1 chosen from 1 choice
[  497.834867] usbcore: registered new interface driver usbserial
[  497.835749] USB Serial support registered for generic
[  497.836053] usbcore: registered new interface driver usbserial_generic
[  497.836062] usbserial: USB Serial Driver core
[  497.845964] USB Serial support registered for pl2303
[  497.846857] pl2303 1-1.4:1.0: pl2303 converter detected
[  497.848947] usb 1-1.4: pl2303 converter now attached to ttyUSB0
[  497.848989] usbcore: registered new interface driver pl2303
[  497.848994] pl2303: Prolific PL2303 USB to serial adaptor driver

---

### Post by grackleman on 2011-05-25
Hi
Have you tried:

sudo ln -s /dev/ttyUSB0 /dev/ttyS0

---

