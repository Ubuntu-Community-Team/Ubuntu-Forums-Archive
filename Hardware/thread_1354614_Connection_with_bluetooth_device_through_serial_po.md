---
title: "Connection with bluetooth device through serial port is losing data"
date: 2009-12-14
forum: Hardware
---

### Post by Rorsch on 2009-12-14
Hello,

I just installed Ubuntu 9.10 and Blueman, and I'm trying to connect a bluetooth device ([SHAKE](http://code.google.com/p/shake-drivers/)) through the serial port. I can't pair the device since it has no alphanumeric input or visual output.

Using Blueman, the device is connected in the **rfcomm0** port, and Signal Strenght is at 50% *(Optimal)*, the Quality of the Connection is at 100%, and the Level of Transmission is at 50% *(Optimal) *.

The problem is the connection itself is losing data in someway. My device's led is purple, indicating that: *(...) packets are being lost due to bad connection or too high data rate.* Since the quality of the connection is presented at 100%, must be the data rate. 

In my device's manual it states that in the port settings I need to have 230400 *Bits per Second*. Anyone knows how do I check such port settings? And if the problem might really be that?

---

