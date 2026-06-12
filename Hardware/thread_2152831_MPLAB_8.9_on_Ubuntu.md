---
title: "MPLAB 8.9 on Ubuntu"
date: 2013-06-09
forum: Hardware
---

### Post by caiorrs on 2013-06-09
Hi guys,

I'm starting developing programs for microcontrolers and I use a PIC16F690, of Microchip.
I want to install the IDE platform on Ubuntu, cause I need to go windows when I want to develop. Is there anything that I can do?

I tried to install it trough the wine, but it returned an error.

Is there a linux version of mplab?

thanks for replies =D

---

### Post by kotkis on 2013-06-10
Generally MPLAB works on wine but it's not advisable - at least its too laggy.
You can try MPLAB-X  ( [http://www.microchip.com/pagehandler/en-us/family/mplabx/](http://www.microchip.com/pagehandler/en-us/family/mplabx/) ) multyplatform IDE from Microchip, based on Netbeans.
Support for the most of the programmers is added, so its usable.
For PIC16 you dont need compiler, but for higher lines you have to use XC compilers from microchip, instead of MCC18/24.

Regards

---

### Post by caiorrs on 2013-06-11
thanks, i installed mplabX but i dont really know how to use it, i just know how to use mplab 8.9, that's very simple to me, otherwise, MPLabX i've never used it before... D=

---

