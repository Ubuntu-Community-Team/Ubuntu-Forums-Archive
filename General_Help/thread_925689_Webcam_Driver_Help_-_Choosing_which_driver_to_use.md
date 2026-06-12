---
title: "Webcam Driver Help - Choosing which driver to use?"
date: 2008-09-20
forum: General Help
---

### Post by frith on 2008-09-20
I have a webcam that I bought off eBay for some insignificant amount (hey, I'm a student...)

Rather stupidly, I didn't check to see if it would work with Ubuntu first - everything else seems to work pretty easily, so I guess I got complacent :)

Anyhoo, it doesn't work. And I have a feeling it will not be working in the near future, because when I plug it in the device is not recognised in any way shape or form.

By that I mean I can plug it in and lsusb reveals:

> lsusb
> 1b17:6111

So I get the device IDs, but it doesn't 'know' what this device is.

My question is this: Is it possible to (manually?) select the driver to associate with a particular device/device ID? I have a feeling this webcam might work with the same drivers that others have (why reinvent the wheel?), but I don't know how to 'force this driver'.

I also suggest, that if this cannot be done, it might be something worth looking into as a future feature - it might not be useful in many situations, but it would be handy to be able to just try a bunch of drivers on a device and see what happens - that might even give someone smarter than me a starting point on writing a driver for a new device...

Frith

---

