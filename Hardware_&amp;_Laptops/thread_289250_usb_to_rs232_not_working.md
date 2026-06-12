---
title: "usb to rs232 not working"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by cmart on 2006-10-30
Hi

I need to connect a GPS to my laptop through usb por, so i bought a usb to rs232(serial) adapter, but i'm unable to mke it work.

this is the **lsusb** output related to it.

Bus 001 Device 009: ID 058f:9720 Alcor Micro Corp.


and **dmesg** output after i connetc it

[17217209.168000] usb 1-5: USB disconnect, address 9
[17217211.236000] usb 1-5: new full speed USB device using ohci_hcd and address 11
[17217211.440000] drivers/usb/class/cdc-acm.c: This device cannot do calls on its own. It is no modem.
[17217211.440000] cdc_acm 1-5:1.0: ttyACM0: USB ACM device

After googling a few hours i found this post related i found this post

[http://www.qbik.ch/usb/devices/showdev.php?id=3846](http://www.qbik.ch/usb/devices/showdev.php?id=3846)

That says it needs a pl2303 driver (no idea where to find it or how to install it), but in the Alcor corp. site i found it uses an AU9720 bridge, so i'm confused about the chip inside the adapter.

This is all the relevant info i've found.  Pliz, throw some light on this issue. 

Thanks

---

### Post by tfmacz on 2007-03-10
Did you get anywhere with this problem?

I seem to be faced with the same situation.

Thanks...
Ted

---

### Post by newpants2003 on 2007-07-05
> **tfmacz said:**
> Did you get anywhere with this problem?

I seem to be faced with the same situation.

Thanks...
Ted

me too...

---

### Post by geraldm on 2007-07-05
The 'pl2303' driver refers to Prolific chip.  There is documentation on it
in linux/Documentation/usb/usb-serial.txt.  The driver is in the kernel
from pl2303.c, usually as a module.  Your log shows ttyACM0 as the device 
to access it.  Look for a device file /dev/ttyACM0  
You should have it, but if you do not, make it with command mknod.  
I have a device on ttyACM0, but it is a modem, using major 166, minor 0,
a character device.

Gerald

---

### Post by ramjet_1953 on 2007-07-06
Quite often, there is a problem with USB to RS232 converters because a package called [COLOR="Blue"]britty[/COLOR] is loaded by default.

Britty is a braille disply for blind people and seems to conflict with USB to RS232.

Try removing britty and britty-x11 and see if you then have some joy.

Regards,
Roger :cool:

---

