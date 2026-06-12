---
title: "Wireless Printing"
date: 2008-05-10
forum: Hardware
---

### Post by amazoohwawa on 2008-05-10
I have an HP Photosmart 3313 All in One Printer which has the ability to print over a wireless network. I have managed to find a driver for a wired connection "USB cable". i am wondering if anyone knows how to connect to the printer wirelessly!

Thanks,

---

### Post by lswest on 2008-05-10
well, try this:
go to system-->administration-->printing

choose "new printer"

then "LPD/LPR host or printer"

for hostname enter the IP of the wireless printer, then hit "next" and choose your HP USB drivers, then continue and fill in the rest of the descriptions.  Once complete, check the settings so the right trays and so are being used, and see if it prints.  Not sure if it will work, but i imagine the drivers should work for it.

Otherwise check here: [http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

and also, check when you're installing the printer if it has drivers listed under HP for your device, i do believe Ubuntu has HP drivers installed for most devices out of the box.

---

