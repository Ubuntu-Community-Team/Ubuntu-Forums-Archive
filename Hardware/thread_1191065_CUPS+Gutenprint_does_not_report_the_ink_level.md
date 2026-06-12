---
title: "CUPS+Gutenprint does not report the ink level"
date: 2009-06-18
forum: Hardware
---

### Post by corradoventu on 2009-06-18
CUPS+Gutenprint does not report the ink level for Epson Stylus D88

I have a printer Epson Stylus D88 connected via USB
the printer works fine but ...

the following problem happens with Ubuntu Jaunty and with Ubuntu Karmic.

when I go to Printer properties I see:

Printer Proprerties - 'Stylus D88 on localhost'

EPSON Stylus D88
usb://EPSON/Stylus%20D88
Epson Stylus D88 - CUPS+Gutenprint v5.2.3

selecting Ink/Toner Levels I see

Ink/Toner Levels
  Marker levels are not reported for this printer

Status Messages
  There are no status messages for this printer



using escputil I see:

corrado@corradokarmic:~$ sudo escputil -iur /dev/usb/lp0 -q
[sudo] password for corrado: 
         Ink color       Percent remaining
             Black                      98
              Cyan                      38
           Magenta                      40
            Yellow                      40

---

### Post by ktat on 2009-07-02
Thankyou for this thread!!

I have been having trouble with my Epson TX100.  After using synaptic to install **escputil** and typing : **sudo escputil -iur /dev/usb/lp0 -q** into the terminal, I can see that my problem was no ink!

---

