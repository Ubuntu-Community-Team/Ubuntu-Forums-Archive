---
title: "Can't activate bluetooth dongle (Billionton)"
date: 2010-05-14
forum: Hardware
---

### Post by jazzgossen on 2010-05-14
I have a Billionton USB bluetooth dongle that I can't get to work in Ubuntu 9.10. 

It is detected allright, lsusb lists it as 
Bus 004 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
and a bluetooth icon with a red X on it pops up in the tray when I insert it.

However, when I go to the bluetooth settings and click on the big "activate bluetooth" button, nothing happens. The window still says "bluetooth not activated", the button gets greyed out, and then nothing more happens.

What to do? I think it used to work back in Dapper or so, but I haven't used it for a long time.

---

### Post by jazzgossen on 2010-05-14
I've found that I can use the bluetooth dongle from the command line, via hcitool. So the problem seems to be with the Gnome bluetooth-applet rather than the low-level communication.

Still, it would be nice to have the GUI side of things working.

---

