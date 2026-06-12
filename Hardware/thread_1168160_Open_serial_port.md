---
title: "Open serial port"
date: 2009-05-23
forum: Hardware
---

### Post by fferreira on 2009-05-23
Hey,

I am developing program that reads from the Serial Port. For handling the serial port issues I am using pyserial.

My laptop does not have a serial port. This way I need one program that writes on the serial port (For testing) too.

The problem is I can't even open the connection :/ 


```

>>> import serial
>>> ser = serial.Serial()
>>> ser.port= 0
>>> ser.bandrate = 9600
>>> ser.open()
>>> ser.isOpen()
**False**

```

What am I doing wrong?

---

