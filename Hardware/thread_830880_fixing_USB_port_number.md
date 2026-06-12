---
title: "fixing USB port number"
date: 2008-06-16
forum: Hardware
---

### Post by aswin on 2008-06-16
Dear all,
I am presently using two USB sensors on my ubuntu machine. When I plug in the sensors it is detected as /dev/ttyACM0 and /dev/ttyACM1. However, I do not know which is which. So, is it possible that I can fix the port number for each device i.e. /dev/ttyACM0 for sensor1 and /dev/ttyACM1 for sensor2? Can I specify the product id or vendor id so that only that specific hardware is selected and given the fixed port number?

Thanks in Advance
Aswin

---

### Post by lswb on 2008-06-16
You can do this with some udev rules. Here's a good website fo find out how:

[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

If you need more help after reading this post again.

---

### Post by bricedebrignaisplage on 2008-06-29
Thanks lswb for the tip. I didn't know about this and it would be such a nice way of solving  our problem. However, I checked in /sys for the properties of our hardware and it doesn't list anything useful to distinguish 2 of them (serial number is set to 0) :(

So I was thinking that another way would be to identify the device by checking on which USB connector it's plugged. I would like to know if it would be consistent. If I always plug at the same connector would it always appear at the same bus and device number?

I checked that when I plug in and out several time on the same port a thumb drive the device number is increased by one each time, but the bus number is the same. But if I plug it to the port next to it the bus number is also the same.

However in our case, we would boot the computer with the 2 devices already plugged and powered. Would they be consistently assigned the same bus and device number?

Or is there any other trick to identify them?

---

### Post by lswb on 2008-06-30
I don't know enough about how the USB bus is initialized to say if this is feasible or not. You could use the techniques explained in the website (using udevinfo & similar commands) to check further up the device chains for the usb bus, I know that (in my system anyway) they are part of the pci system but where individual connectors can be distinguished, I just don't know. I would try redirecting output from the udevinfo lookup into a file for each usp port, then run diff on the 2 files and hope that you see a persistent difference.

What about the devices themselves? I know that a ttyACMx device is usually created by the cdc-acm module, usually for a usb modem of some kind. Is it possible to configre the devices with some kind of initial state or value that your software could use to distinguish them?

---

