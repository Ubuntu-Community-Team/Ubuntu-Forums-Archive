---
title: "How do I &quot;unbound&quot; a device from usb hid?"
date: 2009-07-02
forum: Hardware
---

### Post by Cracauer on 2009-07-02
Related to my other question:

How do I tell the usb hid to not bound to a particular device?

In the past you did that by adding it to the blacklist inside the usbhid.c file, but this isn't the case anymore in 2.6.28.  There also used to be a module load time option but either version I can't find any information on in.

The device in question is a Huey Colorimeter which incorrectly claims to be a HID and (apparently) is then unable to be used in normal udev rules to give it the expected serial device entry.

---

