---
title: "Serial RS485 / RS232 communication with TDK-Lambda ZUP very slow only in Linux"
date: 2019-10-25
forum: Hardware
---

### Post by LastStarDust on 2019-10-25
[SIZE=3]Hello!

In our experiment, we use many ZUP power supplies to power up the electronics. 
The exact models are TDK-Lambda ZUP80-2.5 and ZUP6-33. They are remotely controlled and monitored by a server running Linux.


The problem is that the serial communication is very slow. By slow I mean that the ZUP baud rate can be set between 300 and 9600. To communicate (almost) reliably with the PSU I have to set the baud rate to the minimum 300 bps.


At first, I was suspecting a hardware or wiring issue but nothing seemed to improve the situation. Then I tested the PSU with the [official proprietary Windows application]("https://www.emea.lambda.tdk.com/uk/KB/ZUP-Driver-Downloads.zip") (using the very same hardware setup) and I could communicate at 9600 baud rate without problems. So the problem lies undoubtedly in the Linux driver or in my code.


The ZUP can communicate with the PC using RS232 or RS485. I tried them both with the same results. I tried to use a cheap RS485-USB adapter, the RS232 serial port of a desktop PC and a professional-grade PCIe RS485 card, all without success.


As a programming language, I am using Python. I tried to use [pyvisapy]("https://pyvisa-py.readthedocs.io/en/latest/") and a scientific software called [Pyrame]("http://llr.in2p3.fr/sites/pyrame/") that essentially provides a wrapper around the `serial` Python module. Should I try with a different language?


Here is a minimal example to show how I am accessing the unit in pyvisapy:
```
#!/usr/bin/env python2
# -*- coding: utf-8 -*-


import visa
from visa import constants
rm = visa.ResourceManager('@py')
inst = rm.open_resource('ASRL/dev/ttyUSB0::INSTR')
inst.baud_rate = 9600 # 300
inst.write_termination = ''
inst.read_termination = '\r\n'
inst.set_visa_attribute(constants.VI_ATTR_ASRL_FLOW_CNTRL, constants.VI_ASRL_FLOW_XON_XOFF)
inst.stop_bits = constants.StopBits.one
inst.parity = constants.Parity.none
inst.data_bits = 8


print(inst.write(":ADR01;"))
print(inst.write(":REV?;"))
print(inst.read())

```
In Linux, the above code works with 300 bps but not with 9600 bps (the situation get worse and worse gradually as I increase the baud rate). Even with 300 bps, sometimes I get some timeout or data corruption errors when sending or receiving long commands.


PS our DAQ runs only in Linux so using Windows is not an option.[/SIZE]

---

