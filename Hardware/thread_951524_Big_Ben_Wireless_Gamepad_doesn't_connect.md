---
title: "Big Ben Wireless Gamepad doesn't connect"
date: 2008-10-18
forum: Hardware
---

### Post by dreamer84 on 2008-10-18
Hallo everyone,
if I plug the USB-Receiver of my Big Ben Wireless Game Pad (which is almost a xbox360-controller) on ubuntu 8.04, it is found immediately


```

$ lsusb
...
Bus 002 Device 016: ID 1a34:0801  
...
$ dmesg | grep input
...
[ 5775.609391] input: ACRUX RF USB GAMEPAD 8206 as /devices/pci0000:00/0000:00:10.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input20
[ 5775.641439] input,hidraw1: USB HID v1.00 Joystick [ACRUX RF USB GAMEPAD 8206] on usb-0000:00:10.1-2.3

```

and jscalibrator correctly recognises the properties of /dev/js0 (7 axis, 10 buttons), but after pressing a button the pad itself just blinks like it doesn't find the receiver. Also the label ACRUX RF USB GAMEPAD 8206 seems strange. The Win-driver from CD (TF0801.Inf) was tested with ndiswrapper and installed correctly but didn't change anything. Does anyone have an idea what to do? It seems like the receiver needs an order to activate.
I also tried ubuntu's xpad module without success. Now before I try [http://ubuntuforums.org/showthread.php?t=825464](http://ubuntuforums.org/showthread.php?t=825464) grumbels xpad-driver I first would like to know whether that try would be worth the pain...
Thanks & regards
dreamer84

---

### Post by dreamer84 on 2008-11-10
restarted thread at gaming & leisure, future informations will be posted there: [http://ubuntuforums.org/showthread.php?t=959127]("http://ubuntuforums.org/showthread.php?t=959127")

---

