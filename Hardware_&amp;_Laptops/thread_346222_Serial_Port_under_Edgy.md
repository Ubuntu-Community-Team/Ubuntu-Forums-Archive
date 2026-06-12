---
title: "Serial Port under Edgy"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by freesun on 2007-01-25
I am doing bachelor work in Java under Edgy. I am trying to (as part of work) communicate with serial port device. I am going through USB->Serial adaptor. It is recognized and working. But when I try to open port it says "Not all params are supported by kernel".
This is settings I use (and is for sure correct with this serial plotter):
Baud rate 9600
Data bits 8 bit
Stop bits 1 bit
Parity None

is this unsupported in 2.6 kernel?

thanks

---

### Post by arnor on 2007-01-25
Hello,
Im also developping with Java a RS232 programm...which api do you use? I use javax.comm...

---

### Post by freesun on 2007-01-25
I also use javax.comm version 3.0 (windows only has som 2.x avaible)
I am trying to write to serial plotter. if you send me mail and you will you can help if it works for you.

---

### Post by __j__ on 2007-05-11
I know this thread is a bit old but I'll post a bit of info in the event that it helps someone.

This problem appears to be common (if not unavoidable) with the Sun javax.comm 3.0 package on Linux. The source code to this package is not available so the cause isn't apparent.

The behavior is consistent however: settings calls such as setSerialPortParams() fail the first time, but succeed subsequently. While admittedly inelegant, a workaround is simple: wrap the call in a try block, discard the first exception, then make the call again.

---

### Post by freesun on 2007-05-12
Well the thing got solved. Dunno how. I use HW rs-232 now. And it works. Dunno why. Using javax.comm 3.0 update 1...

---

