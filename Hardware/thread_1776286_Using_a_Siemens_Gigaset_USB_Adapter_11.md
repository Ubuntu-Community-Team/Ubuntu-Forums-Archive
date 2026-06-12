---
title: "Using a Siemens Gigaset USB Adapter 11"
date: 2011-06-05
forum: Hardware
---

### Post by erd11 on 2011-06-05
Hello,
I'm new to the Linux world and I want to use a Siemens Gigaset  USB Adapter 11 for a wireless internet connection on Ubuntu 11.04.  Through some Google research I found a forum thread with somebody having  the same problem as I have, but nobody could solve it. I found out that  Ubuntu seems to recognize the stick as having a Atmel 76c50 chipset  (lsmod shows this: mac80211              204922  1 at76c50x_usb). So  actually it should work since there is a driver for the stick? But, it  doesn't (iwconfig shows that there is no wireless network interface).

I  just came across this page which seems to confirm that the stick should  actually be supported and it should be running out of the box?
[http://at76c503a.berlios.de/devices.html](http://at76c503a.berlios.de/devices.html)
(Have a look at row 98.)

Thanks for your help,
erd

---

### Post by erd11 on 2011-06-06
I found this in the dmesg output. And I'm trying now to install it.

```
[ 1368.745150] Atmel at76x USB Wireless LAN Driver 0.17 loading
[ 1368.759852] usb 2-2: firmware atmel_at76c503-rfmd.bin not found!
[ 1368.759861] usb 2-2: you may need to download the firmware from http://developer.berlios.de/projects/at76c503a/
[ 1368.759879] at76c50x-usb: probe of 2-2:1.0 failed with error -2
[ 1368.759921] usbcore: registered new interface driver at76c50x-usb

```

---

### Post by erd11 on 2011-06-06
I couldn't get it compiled. Can somebody help me compiling it under Ubuntu 11.04?

---

