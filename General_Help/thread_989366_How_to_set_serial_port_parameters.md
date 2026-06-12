---
title: "How to set serial port parameters?"
date: 2008-11-21
forum: General Help
---

### Post by Krupski on 2008-11-21
Hi all,

I have a USB to Serial adapter based on the Prolific PL-2303 chipset. It works like a charm in my Ubuntu 8.10 64 bit desktop and shows up as "/dev/ttyUSB0".

What I want to do is be able to set and change parameters such as baud rate, stop bits, parity, etc...

Before you say "man stty", please be aware that stty DOES NOT work with this device (the PL-2303).

It works with regular 16550 based UART serial ports, but not with the Prolific chipset.

I know that support is "generic" because terminal programs such as "minicom" can change all the settings just fine.

The reason I need to make changes is that I am using the port "directly". That is, I'm doing this (pseudo "code"):

* Edit microcontroller source code (in Linux)
* Compile microcontroller code to binary (in Linux)
* Echo a "stop" > /dev/ttyUSB0 (to the microcontroller)
* Echo a "load" command > /dev/ttyUSB0
* Cat "compiled-code" > /dev/ttyUSB0
* Echo "execute" > /dev/ttyUSB0


This is all inside a BASH script... I don't want to use a terminal.

Of course, what I want to do is SET the serial port parameters before using the port, since my microcontroller can take in data at 115K baud and it's a pain to be stuck at the default of 9600.

OR... if there's a "conf" file for the serial port, I wouldn't mind modifying it's numbers... whatever works.

Thanks!

-- Roger

---

### Post by Wayne_V on 2008-11-21
does it work with setserial/getserial ?

---

### Post by Krupski on 2008-11-21
> **Wayne_V said:**
> does it work with setserial/getserial ?

Nope. Here's what it does:

On-board 16550 type serial port:

```

root@michael:/# setserial  -a /dev/ttyS0
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
Baud_base: 115200, close_delay: 50, divisor: 0
closing_wait: 3000
Flags: spd_normal skip_test

```

My USB-to-serial adapter:

```

root@michael:/# setserial  -a /dev/ttyUSB0 
Cannot get serial info: Invalid argument

```

Strange, huh?

---

