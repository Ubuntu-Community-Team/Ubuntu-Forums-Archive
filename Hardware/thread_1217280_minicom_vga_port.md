---
title: "minicom vga port"
date: 2009-07-19
forum: Hardware
---

### Post by kauboy on 2009-07-19
Hello everyone,
I'm in need of accessing the SVGA port on my HP laptop using minicom to send commands to an externally connected hardware setup. I'm having trouble figuring out the port name I must use under minicom to access the SVGA port if at all it is possible to do so. For example, in minicom, I use /dev/ttyACM0 to access my phone connected to the PC via USB. What should I use for the SVGA port? It's that 15 pin port on the laptop, if I got the name wrong.

---

### Post by lswb on 2009-07-19
Minicom is a program for communication with serial ports, not VGA hardware. Serial port connectors usually have 9 pins, sometimes 25. The 15 pin connector is for an external monitor.

---

