---
title: "USB to SERIAL converter"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by shriphani on 2007-06-17
Can anyone recommend to me a USB to SERIAL converter like --> [http://www.proporta.com/F02/PPF02P05.php?t_id=160&t_mode=des](http://www.proporta.com/F02/PPF02P05.php?t_id=160&t_mode=des) with the appropriate linux drivers ? I would like one as I am missing a COM port which doesn't allow me to sync my multimeter with my laptop.

---

### Post by IntuitiveNipple on 2007-06-17
Interesting question!

I dug out an old Targus USB Port Adapter PA088 (USB to DB9-male Serial port) that comes with a Windows driver disk. As soon as I plugged in I saw:
```
[41784.492000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[41785.288000] usb 1-2: configuration #1 chosen from 1 choice
[41785.452000] usbcore: registered new interface driver usbserial
[41785.452000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[41785.452000] usbcore: registered new interface driver usbserial_generic
[41785.452000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[41785.456000] drivers/usb/serial/usb-serial.c: USB Serial support registered for MCT U232
[41785.456000] mct_u232 1-2:1.0: MCT U232 converter detected
[41785.456000] usb 1-2: MCT U232 converter now attached to ttyUSB0
[41785.456000] usbcore: registered new interface driver mct_u232
[41785.456000] drivers/usb/serial/mct_u232.c: Magic Control Technology USB-RS232 converter driver z2.0
```
and the Link-LED lit up.

---

