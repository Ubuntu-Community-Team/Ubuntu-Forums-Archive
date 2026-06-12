---
title: "Communicating via USB-&gt;RS232 converter"
date: 2013-04-14
forum: Hardware
---

### Post by szafran on 2013-04-14
Hi,

I have a digital thermometer module that connects to PC via USB and has a USB->RS232 converter.
I can connect to it with cutecom (see attachement), but I have no idea on how can I do it from a script (and that's what I need - cutecom was just to check if the module works).
So I need to:
1) Setup a com connect on /dev/ttyUSB0 using specs from the screenshot
2) Send >T to the module
3) Get back the readings from the module.

How to do that ?

P.S.
I've tried `screen /dev/ttyUSB0 19200` and it connects, and also >T works just fine, so I'm 100% sure that the module works.

---

