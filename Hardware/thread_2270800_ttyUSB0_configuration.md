---
title: "ttyUSB0 configuration"
date: 2015-03-25
forum: Hardware
---

### Post by geohei on 2015-03-25
Hi.

Ubuntu 14.04 server amd64.

This might be hardware related. Not sure though ...

I have a serial device (house automation) which is hooked up to the USB port. The software I use uses /dev/ttyUSB0 to address the serial device.

Now ... when the software addresses the device, I get an answer in #40ms. For testing purpose, I put an old passive USB hub (from Sitecom) in between the PC and the serial device. After this intervention, the software accesses the serial device in #5 ms!

How is it possible that putting an USB hub as additional (time consuming) hardware between the PC and the serial device, that the response time is reduced?

Is this possibly due to different drivers being used?

Or are the ttyUSB0 settings different than with/without this hub?

I don't get this.

Also, I noticed that this behaviour doesn't occur with every USB hub.

Any ideas ... ?

---

### Post by geohei on 2015-03-26
No answer ... was the question unclear?
Shall I rephrase?

---

