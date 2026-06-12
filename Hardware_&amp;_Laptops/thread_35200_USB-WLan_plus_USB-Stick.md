---
title: "USB-WLan plus USB-Stick"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by crazy-flash on 2005-05-18
Hi there,
I installed Ubuntu on my girlfriends box, she has a onboard wlan adpater rt2500 (which is connected via the USB-Bus).
I am using 2.6.10-5-386 kernel with ndiswrapper-1.2rc1 with rt2500usb-2.00.01.0000 (03/12/2005).
The wlan connection works fine, until i plug in an usb-stick, then the wlan hangs for a short moment (5 seconds) and the usb-stick will NOT mount. Then when I remove the USB-Stick the wlan connection ___ up (There is nothing more I can do with it, when opening network-properties it hangs, rmmod ndiswrapper hangs, lsusb hangs ...). also there is no way to access the usb-stick ...

---

### Post by crazy-flash on 2005-05-18
Just found out when having usb-stick inserted before booting its mounted fine + wlan works. but removing and plugging in again leads to the same problems.
also its a bit strange: her harddisk is /dev/sda and normally sdb sdc and sdd should be her other sata channels. when plugged in usbstick before booting she gets the devices: /dev/sda (the hardisk) /dev/sdb (the usbdisk) and then sdc sdb sde the other sata channels.

I give you some dmesg stuff, dont know if that can help:

I made the same test twice, both tests leading to different results.
(I always bootet up the system without usbstick plugged)

**TEST 1** 
[INDENT]
a) before plugging in usbstick [dmesg](http://mrclan.bootet.net/temp/test1/1dmesg.txt) [lsusb](http://mrclan.bootet.net/temp/test1/1lsusb.txt)
wlan works

b) after plugging in usbstick [dmesg](http://mrclan.bootet.net/temp/test1/2dmesg.txt)
strangely this time both works: wlan and usbstick

c) after removing and plugging in usbstick again [dmesg](http://mrclan.bootet.net/temp/test1/3dmesg.txt)
usbstick does not work anymore , wlan works

d) after removing usbstick [dmesg](http://mrclan.bootet.net/temp/test1/4dmesg.txt)
after removing usbstick wlan does also not work anymore
     
e) after plugging in usbstick again [dmesg](http://mrclan.bootet.net/temp/test1/5dmesg.txt) [lsusb](http://mrclan.bootet.net/temp/test1/5lsusb.txt)
now usbstick does work well, but wlan forever killed
[/INDENT]

**TEST 2** 
[INDENT]
a) before plugging in usbstiick [dmesg](http://mrclan.bootet.net/temp/test2/1dmesg.txt) [lsusb](http://mrclan.bootet.net/temp/test2/1lsusb.txt)
wlan works

b) after plugging in usbstick [dmesg](http://mrclan.bootet.net/temp/test2/2dmesg.txt)
nothing works, tried lsusb -> hangs

c) after removing usbstick [dmesg](http://mrclan.bootet.net/temp/test2/3dmesg.txt)
nothing works, lsusb still hangs. no way to get usbstick or wlan working
[/INDENT]

---

### Post by crazy-flash on 2005-05-18
anyone???

---

