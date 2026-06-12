---
title: "How To Force USB Modem To Use Same TTYUSB Number?"
date: 2012-08-10
forum: Hardware
---

### Post by robson9776 on 2012-08-10
Hi guys,

I'm using gammu with multiple Huawei 3G modems attached and I really have a problem with it. Gammu configuration file always 'see' those modems as /dev/ttyXXX, but every time I reboot my Ubuntu, those /dev/ttyXXX number always changed.

for example :
I have Modem A with phone number 555-123 attach on USB port and Gammu recognize this device as /dev/tty0.

on the other port, I also have Modem B with phone number 555-999 and Gammu recognize this as /dev/tty3.

when I reboot.... some times /dev/tty0 becomes Modem B and vice versa.

how to force USB PORT A (not Modem A) as /dev/tty0 so that no matter what kind of modems attached on it, Gammu will recognize as a same device? :confused:

I heard by using udev will solve this problem. but I don't know how to use udev, any clue?

---

### Post by Grenage on 2012-08-10
You might need to create your own UDEV rules, that would allow you to specify by ID - I believe!

---

### Post by Whoopie on 2012-08-10
This might help: [http://hintshop.ludvig.co.nz/show/persistent-names-usb-serial-devices/](http://hintshop.ludvig.co.nz/show/persistent-names-usb-serial-devices/)

---

### Post by robson9776 on 2012-08-10
> **Whoopie said:**
> This might help: [http://hintshop.ludvig.co.nz/show/persistent-names-usb-serial-devices/](http://hintshop.ludvig.co.nz/show/persistent-names-usb-serial-devices/)

that's the answer I'm looking for... thanks bro! :popcorn:

---

