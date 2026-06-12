---
title: "Novatel MC950D Wireless Modem"
date: 2010-08-16
forum: Hardware
---

### Post by M_Mynaardt on 2010-08-16
Does anyone how to get this wireless modem from Novatel (model MC950D) working?  I tried to follow the directions I was sent from Novatel's site, but no such luck!

It all started going amiss with the terminal line commands not fulfilling their promise (as such).

What I was supposed to do, apparently, was:

**[COLOR="Navy"]sudo modprobe –r usbserial[/COLOR]**
[INDENT]*(then enter my password)*[/INDENT]

**[COLOR="Navy"]sudo modprobe usbserial vendor=0x1410 product=0x4400[/COLOR]** 
*[INDENT](to load the generic driver)[/INDENT]*

**[COLOR="Navy"]sudo dmesg | grep –i ttyUSB[/COLOR]**
*[INDENT](to verify the driver commands)[/INDENT]*

I was _suppossed_ to get results like this:
[COLOR="Navy"][B][INDENT]usb 5-1: generic converter now attached to ttyUSB0
usb 5-1: generic converter now attached to ttyUSB1[/INDENT][/B][/COLOR]

But nothing happened!  :mad:

Has anyone out there had success getting this wireless modem to work on Ubuntu that can give me some pointers?

Thanks!

---

