---
title: "HP USB Printer not found"
date: 2010-01-05
forum: Hardware
---

### Post by Diphallia on 2010-01-05
Just switched over to Ubuntu and almost everything has been a breeze.
Except for maybe two twings: Flash, players and games flicker (black boxes appear and dissapear for very brief moments, 1 frame at a time or so).


But the main problem is printing.
Ubuntu doesn&#836;'t even recognize that the printer is plugged into the usb port.
It's a HP Photosmart 3310.
Installing hplip didn't help. It couldn't find the printer either.

Also, I'm a noob at Ubuntu since I switched just yesterday.

---

### Post by Diphallia on 2010-01-05
a bumpetibump.

---

### Post by Diphallia on 2010-01-05
I've tried with different cables and tried turning it off and on and all that.
But ubuntu still can't find it.
I have no idea why. The USB-port works fine for other stuff and I've even tried the port in the front panel with no sucess.
It'd be a huge bummer if I can't use Ubuntu just because of this.

---

### Post by pricetech on 2010-01-05
Have you searched the forums, or anywhere else, for information on HP printers under Ubuntu ??  HP tends to be well supported.

Probably take less time and be more productive than bumping your thread.

---

### Post by Diphallia on 2010-01-05
I searched for an hour or two before even considering making a thread.
There's nothing wrong with the printer software, it probably works fine.

---

### Post by Quilan on 2010-01-06
found this:

[http://www.openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_3310](http://www.openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_3310)

hth :¬)

---

### Post by steveneddy on 2010-01-06
If you installed hplip from the repos, uninstall it and install HPLIP from HP:

[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

Trust me, it just works better.

follow the printer set up in the newly installed HPLIP and all should be good.

If you doo all of this and there is still no printer love, please post the output of:

```
lsusb
```

while the printer is plugged and turned on.

---

### Post by Quilan on 2010-01-06
yep, steveneddy, i guess i should have included that link as well. my hp photosmart b109n wireless printer needed the new hplip too :¬)

good luck diphallia :¬)

---

### Post by Diphallia on 2010-01-06
> **steveneddy said:**
> If you installed hplip from the repos, uninstall it and install HPLIP from HP:
[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

please post the output of:
```
lsusb
```while the printer is plugged and turned on.


I did actually install it from HP. What is the repos?

Oh anyway, here's the output.

```
Bus 003 Device 002: ID 03f0:0b0c Hewlett-Packard Wireless Keyboard and Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 03f0:070c Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
```The other HP (the one that's not my mouse and keyboard) is my external hard drive.

---

