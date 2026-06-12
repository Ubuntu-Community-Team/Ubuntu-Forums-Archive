---
title: "FTDI RS232 USB Chip, /dev/ttyUSB0 blocked"
date: 2010-10-28
forum: Hardware
---

### Post by dwvm3 on 2010-10-28
Hello everyone,

I have a very strange problem. I'm using an Arduino microcontroller with a buid in FTDIRS232 chip to send serial data to a Ubuntu 10.04 system. I start Ubuntu, plug in the controller, open a console and type "screen /dev/ttyUSB0 9600" and everything is working as expected. I can see the data.

Then I shutdown the Ubuntu PC and switch the power of. The controller is still connected to the PC. I restart the PC and type "screen /dev/ttyUSB0 9600" again and it tells me that it can not open /dev/ttyUSB0. Disconnecting the controller and connecting it again and everything is working.

So my question is: what is using/blocking /dev/ttyUSB0 if the device is attached during boot.

Thanks in advance

Dierk

---

### Post by dwvm3 on 2010-10-29
I have removed brltty, but this does not help.

---

### Post by dwvm3 on 2010-10-29
If I use the Arduino IDE 0018 to flash the Controller, everything is working as expected, so I think the Arduino 0021 IDE is the problem

---

