---
title: "Using a Socket dual and Quad serial I/O card"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by aerosuraj on 2007-05-22
Hi,
  I am trying to make a Socket Communications based serial expansion card work with a PC running Ubuntu 5.10 Server. The output of the command cardctl ident reports the following-

Socket 1:
  product info: "Socket", "Quad I/O Card Rev 2.1"
  manfid: 0x0104, 0x00a1
  function: 2 (serial)

However, when I eject and insert the card only one COM port shows up.
[4308757.476000] ttyS24: detected caps 00000700 should be 00000100
[4308757.476000] ttyS24 at I/O 0x140 (irq = 10) is a 16C950/954

The serial port is associated with the serial_cs module. How can I make the other COM ports also available?

I have read the following post [http://help.lockergnome.com/linux/Help-PCMCIA-modem-ftopict383078.html](http://help.lockergnome.com/linux/Help-PCMCIA-modem-ftopict383078.html)
which talks about finding the "resources of the card"? What does this mean and is this required in my case?

Alternatively, is there any similar card which is just plug-and-play in Ubuntu? If not, why?

Any help will be greatly appreciated. Thanks.








[http://www.socketmobile.com/products/device-connectivity/serial/](http://www.socketmobile.com/products/device-connectivity/serial/)

---

