---
title: "Bluetooth dongle doesn't turn on at startup"
date: 2010-03-12
forum: Hardware
---

### Post by EsbenSloth on 2010-03-12
My Bluetooth dongle doesn't turn on when I start my system. 
From what I've been able to google 'hciconfig up' should turn it on, but it doesn't do anything, yet 'lsusb' finds the device just fine and it works if I unplug and replug the dongle while my computer is on.
 
[FONT=Fixedsys]lsusb[/FONT] says 

[FONT=Fixedsys]Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)[/FONT]

and [FONT=Fixedsys]hciconfig[/FONT] says 

[FONT=Fixedsys]  BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
  DOWN 
  RX bytes:0 acl:0 sco:0 events:0 errors:0
  TX bytes:0 acl:0 sco:0 commands:0 errors:0

[/FONT]Any ideas on how I can get it to start when I turn on my computer?
Or is there a command that can make the usb bus act as if it was just hot-plugged so I don't have to get down under my desk to turn it on? :?
I'm using Karmic btw.

---

