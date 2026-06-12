---
title: "POS thermal printer printing garbage and old receipts"
date: 2016-04-22
forum: Hardware
---

### Post by marko27 on 2016-04-22
I have a problem that I have been trying to solve for a couple of months, but without luck. We have POS computers with integrated thermal printers and both Linux and Windows installations. Linux installations are all Ubuntu.

The main problem is that the integrated thermal printers may randomly start printing old receipts and if CUPS is installed, it will also cause problems. If CUPS is installed and activated, the thermal printers will just output black stripes. No text or nothing else. The only thing what I have found helping, is to disable CUPS and power off the POS computer.

The other problem is the printing of old receipts. Normally the receipts are printed by writing to the USB/COM port at /dev/ttyS4. But sometimes randomly this will not anymore work and all output will come from some internal buffer. Only a power off of the POS computer will help in this case.

The question is, that can this be prevented somehow? Is this a software configuration problem with Ubuntu or could the hardware be malfunctioning? The POS computers are all new, made in China.

---

### Post by marko27 on 2016-04-26
This is the problem that also occurs sometimes. Do anyone here have had this problem and if yes, what is causing it and how can it be avoided?

[IMG]http://oi68.tinypic.com/a1ing0.jpg[/IMG]

---

