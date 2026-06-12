---
title: "USB - TTL Converter Issues..."
date: 2014-07-26
forum: Hardware
---

### Post by roadhog on 2014-07-26
Hi there,

I have recently bought [this]("http://www.amazon.co.uk/gp/product/B008AGDTA4/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1") USB to TTL serial converter cable on Amazon.
I just bought it to get free postage and thought I would use it with my Raspberry Pi.

This adafruit [tutorial]("https://learn.adafruit.com/adafruits-raspberry-pi-lesson-5-using-a-console-cable/software-installation-linux") says to use 'screen' to connect. With the cables plugged in, when I run:
```

sudo screen /dev/ttyUSB0 115200

```

I get an error saying:
```

Cannot exec '/dev/ttyUSB0': No such file or directory.

```

When I plug it in to a USB slot I get:
```

[I]From 'dmesg'
[/I][ 3163.762526] usb 3-3: new full-speed USB device number 2 using xhci_hcd
[ 3163.762705] usb 3-3: Device not responding to set address.
[ 3163.966709] usb 3-3: Device not responding to set address.
[ 3164.170765] usb 3-3: device not accepting address 2, error -71
[ 3164.282989] usb 3-3: new full-speed USB device number 3 using xhci_hcd
[ 3164.283279] usb 3-3: Device not responding to set address.
[ 3164.487170] usb 3-3: Device not responding to set address.
[ 3164.691195] usb 3-3: device not accepting address 3, error -71
[ 3164.803349] usb 3-3: new full-speed USB device number 4 using xhci_hcd
[ 3164.803535] usb 3-3: Device not responding to set address.
[ 3165.007640] usb 3-3: Device not responding to set address.
[ 3165.211650] usb 3-3: device not accepting address 4, error -71
[ 3165.323680] usb 3-3: new full-speed USB device number 5 using xhci_hcd
[ 3165.323821] usb 3-3: Device not responding to set address.
[ 3165.527985] usb 3-3: Device not responding to set address.
[ 3165.731963] usb 3-3: device not accepting address 5, error -71
[ 3165.732086] hub 3-0:1.0: unable to enumerate USB device on port 3

```

I'm not too sure what all of this means: is this unit faulty?
Any ideas would be great!

I am using Ubuntu 14.04 64 bit

Thanks

---

