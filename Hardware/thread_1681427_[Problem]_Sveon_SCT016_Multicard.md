---
title: "[Problem] Sveon SCT016 Multicard"
date: 2011-02-04
forum: Hardware
---

### Post by zofiel on 2011-02-04
Hello all,

First of all,

I bought this card reader and I was disappointed to see that recognized all but the smart card. So here I am, asking for your help:)

the card in question is [http://www.sveon.com/fichaSCT016.html](http://www.sveon.com/fichaSCT016.html)

looks good, and the funny thing is that the card reader works, only that slot.

 If I run the pcsc_scan:

C/SC device scanner
V 1.4.16 (c) 2001-2009, Ludovic Rousseau
Compiled with PC/SC lite version: 1.5.3
Scanning present readers...
Waiting for the first reader...

Lsusb:

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 011: ID 1307:0361 Transcend Information, Inc.
Bus 001 Device 010: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I think the Bus 001 Device 011: ID 1307:0361 Transcend Information, Inc. because if you disconnect does not appear that neither the Genesys Logi 4-port HUB

Bus 004 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard <- My keyboard
Bus 002 Device 002: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer <- another Card reader.

I think that the smart card model is MultiCardHiKey10_361 and I found drivers for mac. i want to know if I can add in the blacklist the transcend Information, inc and how...

Thank you.

---

### Post by andreselsuave on 2011-03-02
Same problem here, with a WOXTER Smartcard reader. :(

---

