---
title: "HPLIP 5012 Error"
date: 2010-06-26
forum: Hardware
---

### Post by ozmav on 2010-06-26
Done a lot of googling to try and resolve the 5012 error reported by HP-Toolbox for my old laserjet.  The lucid live cd works, on initial install it worked and then all of a sudden it didnt.  

Didnt see too many solutions online that appeared to work.

In the interest of hopefully helping others out there scratching their heads here is what resolved my issue:

Downgraded libusb-0.1-4 from version 2:0.1.12-14ubuntu0.1 (in proposed) to 2:0.1.12-14 and reboot. All fixed.

---

### Post by pwebster25 on 2010-11-19
I'm hung up on the same issue but it seems unlikely that this one will work for me, as I am trying to connect to my printer via a network.  I am on wifi and am connecting to a printer on our local LAN, connected by ethernet.

---

