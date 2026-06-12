---
title: "Epson printer ink level"
date: 2012-07-23
forum: Hardware
---

### Post by dargaud on 2012-07-23
Hello all,
I got an Epson Stylus Office B42WD printer to my folks, and it did work fine until it came time to change the ink...

So how do I find out the ink levels in the printer ? There's no individual LED telling you which cartridge to change, unlike other Epson models. 

- CUPS itself doesn't seem to have an ink level option.
- I tried TurboPrint, which I have a license for, and it gave me an ink level reading ONCE (0 black, 13% magenta, 26% yellow, 13% cyan) but now after changing the black, it chows 114% for all 4 and at the same time it contradicts itself with "Ink Out".
- "stylus-toolbox" shows empty levels while lots of error messages go by.
- "mtink" says "no access right to files /dev..." while my user is in the lp group in /etc/group
- I don't know how to use "ink" or "escputil": ```
$ ink -p usb
Could not access '/dev/usb/lp0' or '/dev/usblp0'.
Could not get ink level.
$ find /dev -name "*lp*"
- nothing -
$ escputil -s -P Epson_Stylus_Office_B42WD
Obtenir état demande d'utiliser un périphérique en mode caractère (raw device).

```
The printer in CUPS is defined as usb://EPSON/Stylus%20Office%20B42WD?serial=4D4734593031313566 but I don't see an lp device.
Even after changing the cartridges the ink LED on the printer still blinks. I'm beginning to think the printer is defective.

---

