---
title: "gps and usb"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by jackciabatta on 2006-12-05
Hi,
I've a asus W6A laptop and gps HI-203 (serial gps).
I use edgy with kernel 2.6.17-10-386.

My laptop no have a serial port, so I use serial-usb converter.
When I connect the gps, dmesg show me:

[17182996.448000] usb 1-2: USB disconnect, address 5
[17182998.200000] usb 1-2: new low speed USB device using uhci_hcd and address 6
[17182998.376000] usb 1-2: configuration #1 chosen from 1 choice
[17182998.404000] input: CHESEN PS2 to USB Converter as /class/input/input7
[17182998.404000] input: USB HID v1.10 Keyboard [CHESEN PS2 to USB Converter] on usb-0000:00:1d.0-2
[17182998.432000] input: CHESEN PS2 to USB Converter as /class/input/input8
[17182998.432000] input: USB HID v1.10 Mouse [CHESEN PS2 to USB Converter] on usb-0000:00:1d.0-2

On Fedora using /dev/ttyUSB0 the gps works fine.
But with Ubuntu, which device must I use?

Thank you very much,
Jack

---

