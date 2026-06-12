---
title: "Karmic hangs using serial port !"
date: 2009-11-12
forum: Hardware
---

### Post by arct on 2009-11-12
Hi,

I'm having some serious issues with Ubuntu 9.10 / Karmic when trying to use the serial port.

Tried with the following laptops :
  - Dell Latitude D620 (using the built-in serial port);
  - Dell Latitude E6400 (using a USB to serial adapter).

On the D620, sometimes, when the serial port is connected to a serial device (some UNIX servers as well as in a standard desktop), sometimes, Karmic just hangs (not even responding to the power button). Sometimes, scroll lock and caps lock keep flashing.

On the E6400, well, since it doesn't have a serial port, I have to use a USB->serial adapter. Actually, all I have to do there is plug in the serial->USB adapter, and wait until the system hangs (I don't even have to connect the serial port to another device!)

I searched everywhere I could... And all I was able to find was this similar (but quite different) problem : [https://bugzilla.redhat.com/show_bug.cgi?id=431379](https://bugzilla.redhat.com/show_bug.cgi?id=431379)

Any suggestions??

Thanks!

---

### Post by arct on 2010-02-16
Bump!

---

