---
title: "Integrated Wwan to wotk with Dell M1330 laptop"
date: 2008-06-08
forum: Hardware
---

### Post by de1ta on 2008-06-08
Hi,

I just got a Dell XPS m1330 laptop with integrated mobile broadband and i want to get this working in Ubuntu (Hardy). I have no previous experience with Linux. I have searched the web and read many forums but still can't get this working. If i type lsusb in the terminal i can find out that my device is thisone:

Bus 004 Device 002: ID 413c:8138 Dell Computer Corp.

and it's an Novatel Wireless HSDPA Modem 

If i get this right the modem should act as 3 serial devices and the usbserial module should somehow connect this to ttyUSB0, ttyUSB1, ttyUSB2 and i should use the ttyUSB0 as my modem when using dialing application.

dmesg tells me that usbserial should work:

[   31.476179] usbcore: registered new interface driver usbserial

Using the dialup gives me:

can not find: /dev/usb/ttyUSB0

looking into the /dev directory i am missing the /usb and no other "nod?" has anything with "USB" in the name, so it feels like i am missing some important USB thingy here.

Where should i go from here? Any ides?

---

