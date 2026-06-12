---
title: "Slow jPilot hotsynch to Palm V with USB to serial cable"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by jpmcc on 2005-08-17
I need to hotsynch my Palm V (serial only) with a Toshiba Tecra laptop (USB only), so I bought an Intex USB to RS232 convertor cable (*"supports over 1mbps data transfer rate*"). When I plug it in, /var/log/syslog shows:

```
kernel: usb 3-2: new low speed USB device using uhci_hcd and address 2
kernel: usbhid: probe of 3-2:1.0 failed with error -5
kernel: drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
kernel: usbcore: registered new driver usbserial_generic
kernel: usbcore: registered new driver usbserial
kernel: drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
kernel: drivers/usb/serial/usb-serial.c: USB Serial support registered for DeLorme Earthmate USB
kernel: drivers/usb/serial/usb-serial.c: USB Serial support registered for HID->COM RS232 Adapter
usb.agent[8454]:      cypress_m8: loaded successfully
kernel: cypress 3-2:1.0: HID->COM RS232 Adapter converter detected
kernel: usb 3-2: HID->COM RS232 Adapter converter now attached to ttyUSB0
kernel: usbcore: registered new driver cypress
kernel: drivers/usb/serial/cypress_m8.c: Cypress USB to Serial Driver v1.06
usb.agent[8454]:      usbhid: already loaded
udev[8630]: creating device node '/dev/ttyUSB0'
```
So, I set jPilot to /dev/ttyUSB0 and hotsynch. It works, but only at 9600 baud - if I try and set it faster, it crashes. This means a hotsynch to an Avantgo server takes 30 minutes...

Has anyone managed to get a USB serial connection working faster than 9600? are there any alternatives to the cypress_m8 driver?

Thanks - John
*Ubuntu 5.04 kernel 2.6.10-5-386 *

---

