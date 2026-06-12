---
title: "Disfunctional h'mc Smart Card Reader"
date: 2017-03-27
forum: Hardware
---

### Post by xinuzi on 2017-03-27
Does anyone know how to get [this h'mc Smart Card Reader [COLOR=#2A2B2C][FONT=&quot]HMC-CRID01B[/FONT][/COLOR]](http://www.h-mc.be/?product=hmc-eid-smart-card-reader-sim) to talk to me on Ubuntu 16.4?

It lightens up but it doesn't accept my id.

pcsc_scan output:

*PC/SC device scanner*
*V 1.4.25 (c) 2001-2011, Ludovic Rousseau <ludovic.rousseau@free.fr>*
*Compiled with PC/SC lite version: 1.8.14*
*Using reader plug'n play mechanism*
*Scanning present readers...*
*0: Generic Smart Card Reader Interface [Smart Card Reader Interface] (20070818000000000) 00 00*

*Mon Mar 27 10:03:18 2017*
*Reader 0: Generic Smart Card Reader Interface [Smart Card Reader Interface] (20070818000000000) 00 00*
[I]  Card state: Card removed, 

[/I]Another, cheaper, id card reader, 'ATM Smart Cardreader SPAL001' works just fine on the same Linux system with the same configuration.

The HMC card reader works on Windows 10. Drivers for Windows and Mac in the package. First the card reader didn't accept the id but after a restart it did.

---

### Post by xinuzi on 2017-03-27
Found (the very simple) solution.

**PUSH IN THE CARD HARD ENOUGH**.

When you try to insert your card you get the impression sth blocks it from going in deeper.
So, again, **PUSH HARDER**.

---

### Post by xinuzi on 2017-03-27
(In the meantime I took out my card, tried to reinsert it, hard enough, and it didn't work anymore. It did again when I reopened Ubuntu's eID card reader app, waited for the blue light on the reader, and twisted the ID left-right/up-down a bit whilst inserting it.)

---

