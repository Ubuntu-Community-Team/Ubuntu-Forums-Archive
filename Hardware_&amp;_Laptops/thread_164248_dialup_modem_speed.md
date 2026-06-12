---
title: "dialup modem speed"
date: 2006-04-22
forum: Hardware &amp; Laptops
---

### Post by trailboss on 2006-04-22
Hi,
I have my modem working. It's a US Robotics 56k. But i'm only getting a 9600 connection. I was told my bios is set at that speed and I would have to change it there. I went to bios and I did not see where you can set the serial speed. Do anyone know how to get my modem working correct? at the correct speed?
thanks
Trailboss

---

### Post by az on 2006-04-22
Install setserial and see what it says about the serial port settings.

I don't know of a way to do it in gnome, but HAl should set it up properly.  Using setserial, you will find out what it is set at and try to set it properly by hand,  Then you can file a bug report about it so that HAl does it properly for you.

Example:

sudo setserial -g /dev/ttyS0

---

### Post by AmboyGuy on 2006-04-22
I use Gnome PPP (in the repo's).
Setup > Modem > speed

---

