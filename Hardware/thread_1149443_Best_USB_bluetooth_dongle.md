---
title: "Best USB bluetooth dongle"
date: 2009-05-05
forum: Hardware
---

### Post by salimfadhley on 2009-05-05
Would anybody care to recommend a USB bluetooth dongle - I'm looking for one which will provide trouble-free operation on Jaunty combined with good signal strength. 

I'd also like to use a bluetooth mouse + keyboard... so if anybody has managed to get one to work beautifully (e.g. automatically start-up with no need to manually activate them using a wired keyboard + mouse).

Thanks!

---

### Post by RoboJ1M on 2009-05-05
Don't get a Belkin F8T009.
Does not work with Bluez 4 as far as I can tell.
In fact, it doesn't appear at all now.
Can't wait for somebody to answer. :)

J.

---

### Post by odinb on 2009-05-05
All bluetooth dongles I have tried work out of the box....

They all seem to identify themselves with the same HW even if they are from different manufacturers. Have tried dongles from at least 5 different manufacturers at this point.

They identify themselves as: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

Cheap dongles can be found here: [http://www.dealextreme.com/details.dx/sku.11866~r.27452115](http://www.dealextreme.com/details.dx/sku.11866~r.27452115)

For a bluetooth keyboard, I use this one for my HTPC: [http://snipurl.com/hg8nk](http://snipurl.com/hg8nk)

This works out of the box, even some of the special buttons work under Intrepid, such as the moon will put your machine into sleep mode, the mail icon will start evolution, volume button works if you run analog audio etc...

One thing though, you need to take it out of HCI mode, or you will have a delay on bootup before it starts working.

========================================================================

Fix delay (or not detecting at all in Intrepid) on Logitech DiNovo Edge:

========================================================================

Type this command in a terminal:

	sudo gedit /etc/default/bluetooth



Then look for the line that says:

HID2HCI_ENABLED=1



and change it to this:

HID2HCI_ENABLED=0



Problem solved.

---

### Post by RoboJ1M on 2009-05-06
I have a Belkin F8T013xx1 here at work, I'm going to take that home tonight and try it. Apparently it's a Broadcom chip. Doesn't fill me with confidence.

So, looks like the drivers for CSR work properly?
Shame there is no way to identify easily beyond just buying and hoping.

Anybody else know of a dongle that has a CSR radio?

Ta,

J1M.

---

