---
title: "USB:2:serial connection issue"
date: 2008-10-08
forum: Hardware
---

### Post by vodsdarov on 2008-10-08
Hi!
Since new motherboards hardly include a serial port, I use a USB to serial cable (**edgeport/1**) to connect to my serial devices.
Under Windows it works like a charm, but I've totally deleted that OS from my life and have no intention to return.

Under Ubuntu I'm unable to connect to my serial devices.
Prior to posting, I've been reading & trying different approaches for a few days. I've seen that kernel 2.6 already includes the driver for USB to serial converters, and apparently it should automount it in the node /dev/ttyUSB0. It doesn't happen to me.

When I list the USB devices, I get:
**lsusb**
```
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0ac8:0302 Z-Star Microelectronics Corp. ZC0302 WebCam
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 1608:0240 Inside Out Networks [hex]   <- THAT'S USB TO SERIAL CABLE
Bus 001 Device 001: ID 0000:0000
```


And when I list the tty nodes (*result as attached text file*)
**ls -al /dev/tty***
No ttyUSB0 node appears

What should I do to connect to serial devices?
Thanks!

---

### Post by vodsdarov on 2008-11-06
I'll reply myself to close the topic.
I just upgraded to Ubuntu 8.10, and the edgeport works like a charm. Issue solved.

---

