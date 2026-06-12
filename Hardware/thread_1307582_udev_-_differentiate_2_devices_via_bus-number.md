---
title: "udev - differentiate 2 devices via bus-number?"
date: 2009-10-31
forum: Hardware
---

### Post by Catscrash on 2009-10-31
Hi,
i have two different devices, which have same vendor-ID and same product-ID, but i need for both of them to have unique devicenames, which must not switch or change after reboot.

with a usual udev-rule like 
```

KERNEL=="ttyUSB?", ATTRS{idVendor}=="4348", ATTRS{idProduct}=="5523", GROUP="dialout", MODE="0660", NAME="temper"

```
it doesn't work, which makes perfectly sense, but how will it work?

Both devices have their own USB-Port and that won't change, so i thought it would be possible to differentiate them via the bus-numer?

first device always is:
Bus 002 Device 005: ID 4348:5523

second device always is:
Bus 004 Device 002: ID 4348:5523 

is there a way to use that in the udev-rule?

thanks for any help, i will attach "lsusb -v" output of those two devices.

Thanks, Catscrash

---

