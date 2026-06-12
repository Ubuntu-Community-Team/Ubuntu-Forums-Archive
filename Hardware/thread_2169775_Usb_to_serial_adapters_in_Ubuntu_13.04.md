---
title: "Usb to serial adapters in Ubuntu 13.04"
date: 2013-08-23
forum: Hardware
---

### Post by witchbutter on 2013-08-23
I have 2 usb to serial adapters and I have been trying to get either one to work in Ubuntu with no success.  They are an IOGear GUC232A and a Trendnet TU-S9.  

I have seen enterprise linux distributions have been able to get these to work which makes me think there may be a module I need to load but I just do not know the name of or where to look.

On the other hand it could be working and just for some reason Putty for linux can't detect or use the device properly.  When I plug the device in it is immediately added as [FONT=Courier New]/dev/ttyUSB0[/FONT] 
but If I try to open a connection no matter what settings might work I get:
 [FONT=Courier New]"PuTTY Fatal Error Unable to open connection to: Unable to open serial port."[/FONT]  
Maybe I'm too used to the windows way of doing this and should be looking at a different application?

If there is source to work with it is not provided by the vendors.

Is anyone aware of usb to serial device models that do work?

---

### Post by witchbutter on 2013-08-23
Some additional information, the modules are loading.  Both devices are the same chip:
Output of [FONT=Courier New]lsmod | grep pl
pl2303                 17581  0 
usbserial              36911  1 pl2303[/FONT]
Output of [FONT=Courier New]lsusb
Bus 003 Device 008: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port[/FONT]

---

### Post by witchbutter on 2013-08-23
The issue is that root owns the device /dev/ttyUSB0 therefore in order to use the connection the console software must also run as root.  From the terminal: sudo putty  then all console connections work as expected on both devices.

---

