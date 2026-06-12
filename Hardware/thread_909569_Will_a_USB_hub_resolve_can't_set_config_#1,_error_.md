---
title: "Will a USB hub resolve: can't set config #1, error -71"
date: 2008-09-03
forum: Hardware
---

### Post by oz457 on 2008-09-03
When connecting one of my external hard drives, the hard drive won't connect and dmesg reveils the following error:
can't set config #1, error -71

The weird thing is that this happens with 2 of my 4 hard drives. Can someone tell me how to resolve the problem? 
One of the options is bying a new USB hub that will have an external power supply. But is this going to help? 

Thanks for any help.

---

### Post by mrsteveman1 on 2008-09-03
Most of the time bus-powered usb drives don't work on a non-powered hub. Power helps :D

---

### Post by wyliecoyoteuk on 2008-09-03
There is only so much pwer that a passive hub can supply. 
as stated above, many bus powered USB hard drives will not work with an unpowered hub, depends on the type of drive and the efficiency of the enclosure, plus how many other items are plugged into your USB ports.
Remember that the hub has to draw all of it's power from the Motherboard.
I have heard of overused cheap passive Hubs crashing computers. 

For example, if you have a mouse, keyboard and small hard drive connected, that is probably more than enough to cause problems when you plug in something else.

---

### Post by oz457 on 2008-09-03
I'm aware that a non powered USB hub is out of the question... but the error message I get seems to be a power problem... that's the conclusion, as far I have been digging into the problem.
The only thing I cannot understand, why does  this happen with only 2 of the external USB hard drives and with the 2 others everything works fine. Keep in mind that ALL of the external USB hard drives have external power. These 2 external HD that are not working even switching to other USB busses of the laptop. I just don't want to spend money on a USB hub if it is not sure that an external USB hub will help out the error message and make these 2 USB external HD to work properly at USB2 speeds.

---

### Post by mrsteveman1 on 2008-09-03
The typical max power for a usb port is like 500ma, which is not much (around 2.5w @ 5v). This is why you need a powered hub for multiple devices, though mice usually only take 100ma.

Post a section of dmesg right after you plug this usb device in so we can see the whole error section.

---

### Post by oz457 on 2008-09-04
Hello,

This is a copy paste of the endless returning error message when connecting the external hard drive...


[  481.032029] usb 5-8: reset high speed USB device using ehci_hcd and address 1
4
[  504.328030] usb 5-8: USB disconnect, address 14
[  545.192025] usb 5-8: new high speed USB device using ehci_hcd and address 15
[  545.570632] usb 5-8: configuration #1 chosen from 1 choice
[  545.572110] usb 5-8: can't set config #1, error -71
[  552.748041] usb 5-8: USB disconnect, address 15
[  557.924024] usb 5-8: new high speed USB device using ehci_hcd and address 16
[  558.097924] usb 5-8: configuration #1 chosen from 1 choice
[  558.118462] scsi7 : SCSI emulation for USB Mass Storage devices
[  558.128281] usb-storage: device found at 16
[  558.128293] usb-storage: waiting for device to settle before scanning
[  563.128243] usb-storage: device scan complete
[  563.244034] usb 5-8: reset high speed USB device using ehci_hcd and address 1
6
[  563.764032] usb 5-8: device not accepting address 16, error -71
[  563.876024] usb 5-8: reset high speed USB device using ehci_hcd and address 1
6
[  564.124917] usb 5-8: reset high speed USB device using ehci_hcd and address 1
6

---

### Post by uncata on 2008-10-10
Exactly the same error in Intrepid beta with a 250 Mb Samsung USB disk.

---

### Post by Dougle on 2009-07-21
A long USB extension lead will have this effect also.

---

