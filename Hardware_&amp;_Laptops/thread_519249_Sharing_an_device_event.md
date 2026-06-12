---
title: "Sharing an device event"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by Azathoth_ on 2007-08-06
Hi, i have been some days trying different configs of the .config file to compile a 2.6.22 kernel and i cannot get in any kernel LIRC working.

The IR device is always been using by another daemon and LIRC needs full access to the event. It is in /dev/hiddev0 and, when o try:

```
sudo lircd -n -H dev/input -d /dev/hiddev0 /etc/lirc/lircd.conf
```

I get:

> lircd-0.8.2-CVS[29445]: lircd(userspace) ready
lircd-0.8.2-CVS[29445]: accepted new client on /dev/lircd
lircd-0.8.2-CVS[29445]: initializing '/dev/hiddev0'
lircd-0.8.2-CVS[29445]: can't get exclusive access to events comming from `/dev/hiddev0' interface

dmesg output is:

> hiddev0: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:1d.2-2
usbcore: registered new interface driver usbhid
drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

Can anyone help me telling me how can i discover which daemon or module is using it or telling me how to share this device.

Thanks a lot

---

### Post by Azathoth_ on 2007-08-07
Can anyone help me?

---

