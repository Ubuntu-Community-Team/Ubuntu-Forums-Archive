---
title: "xbox 360 controller not working"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by pete1 on 2008-01-28
hallo!

First of all sorry about this old topic, but i have read through mostly all artikles written to this topic and i still haven´t found a solution!

 I have tried to compile the driver (xpad.c) and copy it to the kernel input diretory
i have done that with different xpad file, older ones newer ones
and all seems to be fine, but i cant get js0 file in the /dev/input.

i use the dapper drake version update 2 of ubuntu 


list of lsusb:

Bus 002 Device 008: ID 045e:028f Microsoft Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 1267:0212 Logic3 / SpectraVideo plc
Bus 001 Device 001: ID 0000:0000

list of dmesg:

[17182718.120000] usb 2-1: USB disconnect, address 7
[17182869.656000] usbcore: registered new driver xpad
[17182869.656000] /home/peter/xpad1/xpad.c: driver for Xbox controllers v0.1.6
[17182894.868000] usb 2-1: new full speed USB device using uhci_hcd and address 8


as i know there should be a line in dmesg called 
input: joystic Microsoft controller
or something like that 
but i cant find


If anyone can help me please write back!
special thanks

peter

---

### Post by chewit on 2008-01-28
Are you sure that  a new microsoft product which is unlike any other controllers/joystick will work fine with ubuntu

---

