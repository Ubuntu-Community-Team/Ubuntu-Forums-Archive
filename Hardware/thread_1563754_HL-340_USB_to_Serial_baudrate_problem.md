---
title: "HL-340 USB to Serial baudrate problem"
date: 2010-08-29
forum: Hardware
---

### Post by timstewart on 2010-08-29
I have one of these HL340 USB to serial adapters ID: 1a86:7523. When its inserted dmesg reports it and ch341 and usbserial kernel modules are loaded as I would expect. I'm on 2.6.27-17. I am wanting to write a small perl script to send some characters to the serial port, here's a snippet here:```
#!/usr/bin/perl -w
use strict;

use Device::SerialPort;

my $port = Device::SerialPort->new("/dev/ttyUSB0");

$port->baudrate(300);  <<< anything less than 2400bd results in 2400bd
$port->parity("even");
$port->handshake("none");
$port->databits(7);
$port->stopbits(1);
$port->read_char_time(0);
$port->read_const_time(1);

# send data out
$port->write("/?!\r\n");
sleep(1);

```

My problem is that I cannot get the baudrate less than 2400bd. If I set it to anything lower (300,600 or 1200) it still sends at 2400bd. I maybe assuming incorrectly but is the ch341 driver not allowing anything less than 2400bd. If so, is there a reason for this. I've tested the same adapter on XP and the baudrate can be set lower than 2400 with no problems.

Can anyone suggest a different USB to serial adapter that has a driver that allows all the lower baudrates?

Thanks.

---

### Post by timstewart on 2010-08-30
The problem was the ch341 driver.

I redesigned the interface to use a FDTI USB to serial converter and this works ok. Baudrate is now alterable to 300bd.

---

