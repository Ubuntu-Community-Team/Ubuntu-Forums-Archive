---
title: "COM ports in Linux, how do I set them up?"
date: 2013-04-30
forum: Hardware
---

### Post by jlh68 on 2013-04-30
Background:  I have a Weather display station that is connected to my desktop via a Serial port.  The software (Heavy Weather) runs on Windows, so I am using WINE.  This application allows me to select from COM port 1,2,3, or 4, but my Ubuntu OS does not see any COM selections.  I also have a couple of other pieces of hardware that connect via the Serial port.  In fact I have three (3) physical Serial ports on the rear panel of my desktop.

Question:  How do I configure Ubuntu to utilize these Serial ports.  I have seen some sltuff about ttyS but none of it is descriptive enough to help me.

So I would like to have this weather station on one Serial port, my UPS communication link on another Serial port, and the third is for an infrared connection for a fun device.

---

### Post by jonobr on 2013-04-30
Im not sure if this will help you as normally I use the comport to configure stuff or talk to modems, so I am not sure how its going to work for your particular application.

What I can tell you is that on a wiondows box you have Com 1 com2 and so on.
In Ubuntu/Linux its ttyS0, ttyS1 etc.
 to find out what you have, you would rung

dmesg | grep tty

Heres the output from my machine, showing my comports available


[    0.000000] console [tty0] enabled
[    0.533704] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.533824] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.534306] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.534494] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A


tty0 is my virtual console.
ttyS0 and 1 are my comports on my machine


Normally I would use this information for configuration of my ports using minicom, but in your case, Im not sure what is required for that program to work.

---

### Post by tgalati4 on 2013-04-30
Install* setseria*l:

Open a terminal:

```
sudo apt-get install setserial
man setserial
```

---

