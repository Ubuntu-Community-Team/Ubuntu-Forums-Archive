---
title: "USB device not recognized in 7.10"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by timcredible on 2007-10-22
I have an XM PCR that was recognized fine in 6.06, 6.10, and 7.04.  The device would be assigned /dev/ttyUSB0, and xmpcr2 would run the device.  In 7.10, I see the device when I do an lsusb, but it does not get assigned /dev/ttyUSB0 anymore.  I'm using the exact same hardware as before.  Is there a way for me to force this device to be /dev/USB0?  Thanks.

I found the issue - it was with the brltty process that was misinterpreting the device as a braille device and grabbing access to it.  I remove that package, and all is good.

---

