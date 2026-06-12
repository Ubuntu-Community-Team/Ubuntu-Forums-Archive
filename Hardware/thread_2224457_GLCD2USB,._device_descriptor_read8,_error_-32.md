---
title: "GLCD2USB,. device descriptor read/8, error -32"
date: 2014-05-16
forum: Hardware
---

### Post by diyhouse on 2014-05-16
Hope this the correct location,.. ( too many to choose from ), sorry if wrong one.

Any way have built of the Till Harbaum USB monitoring devices. ( see [http://www.harbaum.org/till/glcd2usb/index.shtml](http://www.harbaum.org/till/glcd2usb/index.shtml) )

Basic hardware seems to work OK,.. display shows expected start-up screen, However when I plug the device into a USB port on my  Linuc 12.04 system I get the following:-
[B][ 2757.649643] usb 2-1.8: new low-speed USB device number 27 using ehci-pci
[ 2757.683611] usb 2-1.8: device descriptor read/8, error -32
[ 2757.803493] usb 2-1.8: device descriptor read/8, error -32
[ 2757.905394] hub 2-1:1.0: unable to enumerate USB device on port 8[/B]

I have found one reference to a fix about over current,.. but current for the device is only 32mA @5Volts,.. now I appreciate this is not a start-up current,.. but would be surprised if is was that much bugger, so I don't see this as a viable solution.

Have found some other references on a RasPi website about standards changing but this is dated 2004, ( [http://www.spinics.net/lists/usb/msg02644.html](http://www.spinics.net/lists/usb/msg02644.html) ) so I am slightly sceptical,.. as there are updates for 2011, for this display device.

have also tried on a RasPI device and it to fails the same way...
Does anyone have any ideas,.. or able to shed any light here,

many thanks

---

### Post by diyhouse on 2014-05-21
I have identified the solution to this issue,... problem I was having,. thanks to some pointers from Michael Rogger,.. 

Those who have built these small bits of hardware will be familiar with the small zener diodes on the input lines which act as clamping devices to the incoming,. outgoing signals.
Using large zeners does not work,.. they need to be replaced with smaller 250mW / 0.5W...

I believe this fix works because the smaller Zeners have a smaller inherent capacitance, and thus do not slug the data signal lines,.. and cause timing issues with the sent a received data.

Regards

---

