---
title: "Problems with USB-serial connection and wine"
date: 2009-01-20
forum: Hardware
---

### Post by doctordruidphd on 2009-01-20
I have a scanner (BCD396T) that I am trying to get to work with its
programming software (UASD) running under wine. The software runs and
operates correctly, but I cannot establish a connection to the
scanner. This computer (sony vaio k-23 laptop) has only USB ports, so I have to use a USB-to-serial cable. The scannner uses its own USB to serial cable, with its own specialized connector. The software has only COM1, etc. options available; no /dev/ttyUSB0.

Linux (ubuntu 8.10) does see the cable (as ttyUSB0), and changing the
baud rate within the software does change the port speed, as viewed
with stty. The software just never sees the radio.

lsusb gives the following information about the cable:
Bus 002 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303
Serial Port

I do have the link set up in .wine/dosdevices as follows:
ln -s /dev/ttyUSB0 com5

I have tried other com numbers, up to 8. And baud rates, etc. The
software sees the com port there, just not the radio.

This is really a more general problem than just this software/radio;
several radios I have need to be programmed by Windows software,
through a USB-serial connection. Any suggestions from anyone who has
this, or a similar USB-serial connection, working?

---

### Post by chicorasia on 2009-11-04
This may be helpful:

[http://wiki.jswindle.com/index.php/Wine_Registry#Serial_Com_Port](http://wiki.jswindle.com/index.php/Wine_Registry#Serial_Com_Port)

best regards

---

