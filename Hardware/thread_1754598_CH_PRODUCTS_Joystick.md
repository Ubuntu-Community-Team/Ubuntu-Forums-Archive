---
title: "CH PRODUCTS Joystick"
date: 2011-05-10
forum: Hardware
---

### Post by zmelkoow on 2011-05-10
Hello guys!

I am new to this forum an I really need help with one issue.

I have to install CH Products IP Desktop Joystick on my system.

The joystick is working properly under Ubuntu 8.04.
I need to use Ubuntu 10.04 for this project.
Under Ubuntu 10.4 joystick is detected but OS doesn't recieve any commands from it.

When I plug it in I get : 

[247918.010265] input: CH PRODUCTS CH PRODUCTS IP DESKTOP CONTROLLER as  /devices/pci0000:00/0000:00:16.0/usb7/7-3/7-3:1.0/input/input8
  [247918.010523] generic-usb 0003:068E:00CA.0003: input,hidraw2: USB HID  v1.00 Joystick [CH PRODUCTS CH PRODUCTS IP DESKTOP CONTROLLER] on  usb-0000:00:16.0-3/input0

Even if I try the jstest command I get nothing from it, while on 8.04 I can clearly see commands.

Did anyone experience such problems or knows the solution?

Thank you for your help,

Z

---

### Post by Bill Grabowski on 2011-05-28
I have exactly the same problem with Ubuntu 11.04. 

This is what I had with the CH stick connected:

[ 5415.076123] input: CH PRODUCTS CH FLIGHTSTICK PRO as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input8
[ 5415.076300] generic-usb 0003:068E:00F6.0005: input,hidraw0: USB HID v1.00 Joystick [CH PRODUCTS CH FLIGHTSTICK PRO] on usb-0000:00:1a.1-1/input0

If I plug in my Logitech joystick however, it works fine, with the dmesg output below: 

[ 5445.043105] input: Logitech Logitech Extreme 3D as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input9
[ 5445.043278] logitech 0003:046D:C215.0006: input,hidraw0: USB HID v1.10 Joystick [Logitech Logitech Extreme 3D] on usb-0000:00:1a.1-1/input0

One difference I see is that Unbuntu treats the CH as "generic-usb", but the Logitech as "logitech". Don't know if this is significant or not.

Weird that CH stick would be OK with previous versions of Unbuntu but not 11.04.

Bill

> **zmelkoow said:**
> Hello guys!

I am new to this forum an I really need help with one issue.

I have to install CH Products IP Desktop Joystick on my system.

The joystick is working properly under Ubuntu 8.04.
I need to use Ubuntu 10.04 for this project.
Under Ubuntu 10.4 joystick is detected but OS doesn't recieve any commands from it.

When I plug it in I get : 

[247918.010265] input: CH PRODUCTS CH PRODUCTS IP DESKTOP CONTROLLER as  /devices/pci0000:00/0000:00:16.0/usb7/7-3/7-3:1.0/input/input8
  [247918.010523] generic-usb 0003:068E:00CA.0003: input,hidraw2: USB HID  v1.00 Joystick [CH PRODUCTS CH PRODUCTS IP DESKTOP CONTROLLER] on  usb-0000:00:16.0-3/input0

Even if I try the jstest command I get nothing from it, while on 8.04 I can clearly see commands.

Did anyone experience such problems or knows the solution?

Thank you for your help,

Z

---

