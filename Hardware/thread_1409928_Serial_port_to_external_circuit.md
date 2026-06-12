---
title: "Serial port to external circuit"
date: 2010-02-18
forum: Hardware
---

### Post by Bottone234 on 2010-02-18
I need to switch-on external devices when I start Ubuntu and switch-off when leave Ubuntu.
Can I use serial port and a little electric circuit with a relay?
Thank you

---

### Post by IcarusR on 2010-02-18
I searched for a way to do this sometime ago & found the linked page, however I couldn't get it to work. Maybe you'll have more luck.

[http://www.bolis.com/amillar/electronics/serial-port-control-power-switch]("http://www.bolis.com/amillar/electronics/serial-port-control-power-switch")

---

### Post by tgalati4 on 2010-02-18
Not cheap, but an off-the-shelf product:

[http://www.bomara.com/cps/cps.htm](http://www.bomara.com/cps/cps.htm)

Another way to do it is to use an APC brand UPS.  They come in many flavors with USB, serial, and cat-5 connections.  Using apcupsd, you can do some fancy stuff, including shutting down the UPS itself after a system shutdown.  Then, any devices connected to the UPS will also shut down.

There are also power-sensing power strips.  One plug detects current from an active device and it then turns on the rest of the strip.

Give us some more details on what you are trying to do and folks will chime in with even more creative solutions.

---

