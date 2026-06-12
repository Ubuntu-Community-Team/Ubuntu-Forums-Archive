---
title: "Help needed to get serial interface working with Hosola PV inverter"
date: 2013-11-03
forum: Hardware
---

### Post by sanderj on 2013-11-03
Hi,

Short: I need help to get the serial communication (RS232) working for an undocumented device (Hosola). Tips appreciated

Long:

I have got a Hosola 2.2k TL, which is an inverter for PV solar panels. The device has a RS232 interface. Hosola's documentation says:

> 
8. Communication and Monitoring

8.1 Communication Interface
This product has an communication interface RS232. Operating information like output
voltage, current, frequency, fault information, etc., can be delivered to PC or other
monitoring equipment via RS232.

8.2 Communication
When user want to know the information of the power station and manage the entire
power system. We offer below two types communications.

RS232 Communication
RS232 is one standard communication interface. It transmits the data between PC and
one single inverter (Figure 20).

RS232 Communication Cable and Interface

One inverter can only be communicated with one PC at the same time through RS232 port. Thus this method is generally used for single inverter&#8217;s communication, for examples: software updating and serviceman&#8217;s testing.

And that's it. No further specs about speed, command set or usage.

I connected a USB-to-serial device, which seems to be recognized by Ubuntu:

```
Nov  3 14:28:29 flappie kernel: [130699.956281] usb 2-1.2: ch341-uart converter now attached to ttyUSB0

```
Connection is: Ubuntu-laptop --- USB-to-serial --- RS232-of-Hosola


I've used sudo minicom, picocom and gtkterm against /dev/ttyUSB0, and I tried a lot of combinations (starting with 9600 N81), but pressing ENTER nor pressing other keys gives any reaction.

So ... what could be going on? Is there a way to automatically vary all parameters to see if that matters?

---

