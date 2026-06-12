---
title: "wacom digitizer 2 via serial adapter"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by risto.pekkala on 2007-12-05
Followed some guides and have finaly a device named /dev/ttyUSB0. But then I get:

sudo wacdump /dev/ttyUSB0
WacomOpenTablet: Connection timed out

Are there any baudrate settings to be made?

There is a small switch on the top edge that I cannot remember if it is a powerswitch and what position is "on". Nothing seems to happend when I flip it.

---

### Post by kirys on 2007-12-07
I'have the same problem with a graphire 1 serial :(
Is not a problem of baudrate cause if you use wacdump -v you'll see that it tries with many speeds.
I read somewhere that is a incompatibily issue between kernel 2.6.22 and linuxwacom earlier that 0.7.9.
But I cannot confirm that

Cya

---

