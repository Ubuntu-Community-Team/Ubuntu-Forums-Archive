---
title: "what would be the best 56k modem to use for fax server"
date: 2008-11-13
forum: Hardware
---

### Post by kustomjs on 2008-11-13
Alright Guys
I have been asking this question for over 3 weeks now and I am still not getting any help on my question. my question is what is the best 56k modem to use for a fax server? the reason why I am asking this because I have small business that I run that requires to fax orders in for my vendors.

---

### Post by cariboo on 2008-11-13
There is no best modem for Linux, get one that is supported. Have a look here:

[http://xmodem.org/modems/index.html](http://xmodem.org/modems/index.html)

Check that the modems you are looking at are on the list.

Jim

---

### Post by kustomjs on 2008-11-13
well can I have 2 same modems on the same machine or not? because I just got done buying 2 of these modems: 
Conexant 56k V.92 CX11252-11 PCI Data/Fax Modem (OEM)

what I mean having 2 modems on same machine is

configure one only to send out faxes. then configure the other one for only for incoming faxes.

---

### Post by marinos on 2008-11-13
> what is the best 56k modem to use for a fax 
> server? the reason why I am asking this because 
> I have small business that I run that requires to 
> fax orders in for my vendors

There's no need for a "56k" faxmodem, faxing speeds
are usually restricted to either 9600bps or 
14400bps, so even a very old modem will do.  
For guaranteed compatibility I'd suggest you find 
an external SERIAL faxmodem (this presumes your 
computer does have a serial port.)  These are
"real" hardware faxmodems

Personally, having to send/receive the occasional 
fax every so and then, I've resorted to using an 
ancient external USRobotics Sportster 33.6 serial 
faxmodem which works a charm in Ubuntu with 
the Efax software, for almost two years now.

---

