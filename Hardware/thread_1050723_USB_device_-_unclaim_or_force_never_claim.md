---
title: "USB device - unclaim or force never claim?"
date: 2009-01-25
forum: Hardware
---

### Post by pmgeahan on 2009-01-25
Folks -

I've recently built a USB motion detector, using plans from MAKE magazine.  Great little project.  The project is built around a USB-Micro U421 interface.

The problem I've got comes when I try to drive the device.  I can't claim the USB interface in the driver program; when I do, it fails.  My google-fu seems to show that the OS might already be claiming it, because it thinks it can drive it.  Relevant info:

dmesg output:
```
[773179.309486] usb 5-2: new low speed USB device using uhci_hcd and address 15
[773179.324062] usb 5-2: configuration #1 chosen from 1 choice
[773179.360143] hiddev96hidraw2: USB HID v1.00 Device [USBmicro, L.L.C. U421] on usb-0000:00:1d.0-2

```

The program I'm writing is itself attached.  

So here's my thing - I obviously need to claim this interface somehow, else I can't send or read from it.  So I'm thinking I need to do one of the following three things:

1.  Give my program a way to force the other program to unclaim the device.

2.  Configure Ubuntu to stop claiming it at all(perhaps through udev?)

3.  Figure out some way to read the device state through HID.  I have no idea what this is.  

A developer's notebook for this device is here:

[USB Micro ODN]("http://usbmicro.com/odn/index.html")

The gist of the circuit is that, when the USB motion detector is tripped, it goes high on Port A bit 1.  So realistically, if I can read the state of that bit, then I'm good to go.  

Thanks for your help.  I would've thought the circuit would be the hard part!

---

### Post by pmgeahan on 2009-01-27
OK, I managed to solve my own problem.  

Buried deep within page 10 or 12 of a google search was the note that usb_claim_interface can be affected by permissions.  A quick sudo later, and the device is claiming wonderfully.  

For those of you who may have built the Make Magazine USB motion detector, here's the program I hacked together to read the data.  It's pretty ugly, as I haven't had a chance to clean it up yet.

---

