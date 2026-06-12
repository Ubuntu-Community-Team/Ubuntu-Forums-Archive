---
title: "Wireless Keyboard / Mouse Behavior"
date: 2012-01-20
forum: Hardware
---

### Post by quilaho on 2012-01-20
I have a new wireless keyboard / mouse combo I'm trying to use on my laptop setup. When I plug them in, the system goes a bit bizzerk. 

* Windows close, like Chrome, and when I reopen it I have 2 tab bars across the top and all the pages are blank. Chrome is the only app i've had open long enough to see odd behaviour. Could be Chrome but ...

* When I reboot with the wireless dongle plugged in the Ubuntu signon screen nevr comes up. Sometimes the box will show but nothing else. Then one screen goes blank with purple on the other, then both black, then one purple, repeat with not real pattern. I think it's trying to start X but bombing out.

When I unplug the dongle and reboot, everything goes back to normal.

I've been using Linux (OpenSuse) for many years as my only OS at home. I know my way around but I'm not very proficient at the commands to troublshoot hardware issues. If someone could walk me through some techniques, it would be greatly appreacieated.

The system ...
* Ubuntu 11.10
* HP EliteBook 8440p
* Intel i5 Processor
* Intel Graphics
* Sitting on an HP docking station model VB041UT#ABA. (I have tested this both on and off the docking station)
* Hooked to an HP monitor model LA2205wg via DVI. It's setup dual screen with the laptop screen.
* Keyboard / mouse combo is an HP communication via RF. The box has a part # of BL54944#ABA. The keyboard and mounse have individual part numbers I can supply if someone feels it necessary. The keyboard has another brand of Anatel on the bottom so I'm guessing that is the OEM.

Thanks.

---

### Post by quilaho on 2012-01-22
With some more reading I found reference to the lsusb command. Through it I have identified the device (assuming the dongle) as ...

Bus 002 Device 004: ID 04ca:0055 Lite-On Technology Corp.

I Googled on "04ca:0055 Lite-On Technology Corp" and found the following ...
[http://www.ubuntu.com/certification/catalog/make/usb:04CA](http://www.ubuntu.com/certification/catalog/make/usb:04CA)
[http://cateee.net/lkddb/web-lkddb/DVB_CORE.html](http://cateee.net/lkddb/web-lkddb/DVB_CORE.html)

It looks like this device should be supported under 11.10 through a kernel module of DVB?

---

