---
title: "load multiple modules from /etc/modules"
date: 2012-05-11
forum: Hardware
---

### Post by rymjones222 on 2012-05-11
I am flashing a device which enumerates with different product Ids during the flash process. When connected usbserial is correctly added based on my entry in /etc/modules. Once I flash the device, the device disconnects then reconnects but it doesn't add usbserial again for the newly reported productId. I am assuming it is because I didn't physically disconnect the usb device. Is there any way around having to manually run modprobe for this second step?

---

### Post by rymjones222 on 2012-05-14
usbserial doesn't allow for multiple product ids. so a custom kernel module is required

---

