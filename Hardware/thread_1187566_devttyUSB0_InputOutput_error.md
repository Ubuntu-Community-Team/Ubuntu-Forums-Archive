---
title: "/dev/ttyUSB0 Input/Output error"
date: 2009-06-14
forum: Hardware
---

### Post by siennalizard on 2009-06-14
Hi fellow Ubuntuers,

[I'm using Jaunty, x86, right up-to-date on both the machines below.]

I wrote a system in PHP (using the phpserial class by Rémy Sanchez) to send text messages via a USB GSM modem. It works absolutely fine once I had worked out the flow control problems in talking to the serial port. It is running on an older desktop P4 x86 machine.

Flushed with success, I thought I would install Ubuntu on a laptop (more powerful than the desktop, and much newer). I then installed my PHP system, but after sending one message through the modem all serial commands report "Input/Output error" when trying to connect to the serial port: /dev/ttyUSB0. The only solution is to reboot. Nothing is left in the log to aid me. This is very reproducible: every use of the serial port rapidly renders it unavailable.

I've tried different flow control settings, and I've checked that other processes are not using the device.

Can anyone think why I would get different results on two different computers running the same version of Ubuntu?

Thanks for your thoughts.
J.

---

### Post by franziski on 2010-02-05
phpserial give me several issues like you
so i switched to Perl (better serial management).

---

