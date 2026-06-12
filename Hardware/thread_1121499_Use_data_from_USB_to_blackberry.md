---
title: "Use data from USB to blackberry?"
date: 2009-04-10
forum: Hardware
---

### Post by hanasaki on 2009-04-10
any way to use a blackberry 8800 as the modem for ubuntu to connect via ATT?

---

### Post by steveneddy on 2009-04-11
[http://netdirect.ca/software/packages/barry/](http://netdirect.ca/software/packages/barry/)

---

### Post by hanasaki on 2009-04-15
Great looking stuff!... backup seems to work... Anyone have a script for the BB800 on ATT/Cingular?

the cingular driver looks for a ttyUSB and this does not seem to appear for me
the 02-ireland (comes up as 'orage' and/or 'o2') when in the UK fails on the LC negotiation

---

### Post by Maheriano on 2009-04-15
You don't need a USB cable, the OBEX should work as part of the bluetooth stack wirelessly.

---

### Post by hanasaki on 2009-04-18
Finds the bluetooth and connects
  - poked around for connecting to ATT / including the barry project and a few others
  - no luck so far.
  - any way you know of to use the gnome tools and/or networkmanager to cause it to connect as a modem.  (specifics please?)

[http://sourceforge.net/projects/barry/](http://sourceforge.net/projects/barry/)

---

### Post by Maheriano on 2009-04-19
Once it pairs, manually create a dialup connection and set the modem to your Blackberry. There should be a few in the list and it'll probbaly be listed as General or something. Guess and check to figure out which one it is. Then set the number it dials as #777, and set the username/password. For my carrier my username is [email]mytendigitnumber@1x.telusmobility.com[/email] and my password is the ESN of my phone.

---

