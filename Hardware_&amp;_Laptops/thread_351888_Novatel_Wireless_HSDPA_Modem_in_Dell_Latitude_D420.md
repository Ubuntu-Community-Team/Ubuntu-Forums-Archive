---
title: "Novatel Wireless HSDPA Modem in Dell Latitude D420"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by joncheyne on 2007-02-02
Hi

There is a built in 3g device in the new Dell Latitude's - a Novatel Wireless HSDPA Modem which is showing in the extraction from lsusb attached to this post. It also shows up in the Device manager.

How do I get this device recognised as a Modem? Another thread about a different make of device suggested usbserial and looking for ttyUSB* ... I definitely don't have any of those.

I have googled with no joy - most people are talking about pcmcia cards and inserting to recognise.  Mine is completely built in - no idea how to activate etc.

Clue will be gratefully followed!

Many thanks

Jon

---

### Post by Bubbel on 2007-04-28
Doesn't it make one or more serial ports?

I have an Vodafone PCMCIA Option Card, and it is controlled as a modem on ttyUSB0. If this is the case, you need the correct init string, username/password and telephone number (Something like *99**0 or so).

You can use something like gnome-ppp to do the dial-up.

good luck,

Regards, Bubbel

---

### Post by pbook on 2007-07-07
Have a look at [http://www.net42.co.uk/os/linux/d620_3g_datacard.html](http://www.net42.co.uk/os/linux/d620_3g_datacard.html), be aware to adjust the product nuber with the card you have, It worked for me. Also the this [http://umtsmon.sourceforge.net/](http://umtsmon.sourceforge.net/) worked!
 
I am am using the Nvatel modem with success!.


RS

---

