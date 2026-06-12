---
title: "Two strange lines on top of every print"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by bajun on 2008-01-09
I have printer Epson Stylus Color 300 installed on Ubuntu Gutsy with standart stc300 driver (best print quality).
On top of every print i have two strange lines:

EJL 1284 4
EJL

All lines of all dokuments are moved on two positions downwards.

Seems like service information. This is not a bug but strange issue of standart configuration.
How to fix this?

---

### Post by bajun on 2008-01-09
I deprecate my by bad English, please don't see on stupid errors. 

After searching in internet i have found some fixes, all about to switch the communication mode of parallel ports in bios. I have no parallel ports on my laptop, therefore there is no ability to switch this. My printer is connected through usb to parallel adapter.

I have found [this:]("http://www.undocprint.org/formats/printer_control_languages/ejl")

> **Enter IEEE 1284.4 Command**
This command specifically takes the printer out of the Epson packet mode communication protocol (whatever that is) and enables IEEE 1284.4 communications mode.

Syntax:

```
@EJL<SP>1284.4<LF>~
@EJL<SP><SP><SP><SP><SP><LF>
```

Then I have tried to add the following commands from the ["Details of Ghostscript output devices" article]("http://www.ghostscript.com/doc/7.07/Devices.htm#Uni_all_parameters") in system-config-printer advaced options, without any result:

```
upBeginJobCommand:@
upBeginPageCommand:@
upWroteData:0
```

Any ideas on how to fix this would be great! 
I don't want to bring my good old printer to garbage deponie because of this stupid error.
Very ugly fixes are welcome too, but please not about purchasing of a new printer or adapter. The problem is very actual for me.

---

