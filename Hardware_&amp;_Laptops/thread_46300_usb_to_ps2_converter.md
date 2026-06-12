---
title: "usb to ps2 converter"
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by bmichel on 2005-07-04
Hi,

I've got a new laptop without ps2 ports. So I try an Y usb to ps2 converter to connect a keyboard and a mice. Don't work. any idea?

thanks

---

### Post by ranf on 2005-07-04
[QUOTE=bmichel]
I've got a new laptop without ps2 ports. So I try an Y usb to ps2 converter to connect a keyboard and a mice. Don't work. any idea?
[/QUOTE]

In a terminal type:
```
lsusb
``` 
What do you get?

---

### Post by bmichel on 2005-07-04
without the usb/ps2 connector:
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 1241:1111 Belkin (?) Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

with the usb/ps2 connector:
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 1241:1111 Belkin (?) Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 0518:0001 EzKEY Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

So the connector is well seen but not the peripherals behind

---

### Post by ranf on 2005-07-04
I'd try:
```
sudo tail -f /var/log/messages
``` 

Then unplug and replug your converter and see what you get.
Google around for anything that you get.

---

