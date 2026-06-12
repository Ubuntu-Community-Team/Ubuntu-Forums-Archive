---
title: "Unable to use usb connection on my camera/webcam"
date: 2010-05-08
forum: Hardware
---

### Post by hellocatfood on 2010-05-08
I have a [Medion MD80566 DV Camcorder](http://www.inest.co.uk/products/Medion_MD80566_Mini_DV_Camcorder_-DV-OUT_-_USB-OUT-_Brand_New.asp) and, as well as a dv connection, it comes with a usb connection. The pins on the dv port have broken so I'm trying to get usb working but Ubuntu doesn't recognise it as a camera.

Using tail -f /var/log/messages the computer recognises that it's plugged in:
```
May  9 01:28:29 hellocatfood kernel: [ 5365.100061] usb 7-1: new full speed USB device using uhci_hcd and address 11
May  9 01:28:29 hellocatfood kernel: [ 5365.255087] usb 7-1: config 1 interface 0 altsetting 0 has 3 endpoint descriptors, different from the interface descriptor's value: 2
May  9 01:28:29 hellocatfood kernel: [ 5365.255208] usb 7-1: configuration #1 chosen from 1 choice
```

However, programs like cheese and kdenlive don't recognise it as being a camera.

Is this a driver issue?

---

