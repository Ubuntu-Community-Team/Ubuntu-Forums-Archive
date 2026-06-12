---
title: "CH joysticks not working on Karmic Koala (9.10)?"
date: 2009-12-24
forum: Hardware
---

### Post by akos.maroy on 2009-12-24
I wonder if other people have the same problem: I can't seem to make my CH Fighterstick Pro and my CH Pro Throttle work on my Karmic Koala (9.10) 64 bit system. The CH Pro Pedals joystick seems to work just fine on the same system.

Interestingly, the joysticks do register:

```
[ 2892.341212] usb 2-2.1: new low speed USB device using ehci_hcd and address 26
[ 2892.478972] usb 2-2.1: configuration #1 chosen from 1 choice
[ 2892.581231] generic-usb: probe of 0003:068E:00F3.001C failed with error -71
[ 2905.162801] usb 2-2.1: USB disconnect, address 26
[ 2907.950527] usb 2-2.1: new low speed USB device using ehci_hcd and address 27
[ 2908.089320] usb 2-2.1: configuration #1 chosen from 1 choice
[ 2908.099219] input: CH PRODUCTS CH FIGHTERSTICK USB  as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2.1/2-2.1:1.0/input/input28
[ 2908.099411] generic-usb 0003:068E:00F3.001D: input,hidraw3: USB HID v1.00 Joystick [CH PRODUCTS CH FIGHTERSTICK USB ] on usb-0000:00:04.1-2.1/input0

```

and they do show up using jstest:

```
$ jstest /dev/input/js0 | head
Driver version is 2.1.0.
Joystick (CH PRODUCTS CH FIGHTERSTICK USB ) has 5 axes (X, Y, Z, Hat0X, Hat0Y)
and 19 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4, BaseBtn5, BaseBtn6, BtnDead, BtnA, BtnB, BtnC, BtnX, BtnY, BtnZ).
Testing ... (interrupt to exit)
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:-32767  1:     0  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:-32767  1:-32767  2:     0  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:-32767  1:-32767  2:-32767  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:-32767  1:-32767  2:-32767  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:-32767  1:-32767  2:-32767  3:     0  4:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:oAxes:  0:     0  1:-32767  2ff 14:off 15:off 16:off 17:off 18:off 

```

but no matter how I move the joystick, there's no effect.

this is the case for the CH FigherStick Pro and the CH Pro Throttle. interestingly, a CH Pro Pedal works fine in the same system.

the same joysticks work fine on an Ubuntu 8.10 system.

was there some major change in the kernel that made the joystick not work?

---

