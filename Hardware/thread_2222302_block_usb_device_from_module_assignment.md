---
title: "block usb device from module assignment"
date: 2014-05-05
forum: Hardware
---

### Post by gobo7 on 2014-05-05
i hope this is the best forum to ask.

i need to block udev from assigning ftdi_sio to a particular usb board.
a udev rule was built with OPTIONS+="ignore_device".  it seems ignore_device
has been removed from udev.

what options are available to block udev from grabbing the device?

i don't want to blacklist all ftdi devices, just this one device by
some sort of internal id.

thanks.

---

