---
title: "HP Laserjet printer install"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by Malta paul on 2007-05-20
I've now bought a HP Laserjet 1018 printer.
Using 'Feisty' the printer is detected and installs with driver Foo2zjs, at LPT1 but then will not 'test print' 
[the printer works OK in M$ with Hp drivers -so printer dose work] I have also checked F002zjs.rkkda.com/  still no success. :confused
Anybody had this problem and fixed it?   Thanks folks.

---

### Post by alshurooqi on 2007-05-20
if your printer model is not listed you can try using one of the drivers listed under the Generic manufacturer

---

### Post by jrusso2 on 2007-05-20
Try this

The firmware of the printer must be uploaded after turning it on. You can use a hotplug/udev script which comes with foo2zjs, or do it manually: "cat /usr/share/foo2zjs/firmware/sihp1018.dl >  /dev/usb/lp0".
User Notes


[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018)

---

### Post by Malta paul on 2007-05-21
Thanks guys for your advice, will give them a try when I get home from work,and post back results ;)

---

### Post by Malta paul on 2007-05-21
The printer is working know, I used this link and change the printer name from 1020 to 1018 when I made the terminal entry. [http://stepien.com.pl/2006/09/23/install-your-hp-laserjet-1020-on-ubuntu/](http://stepien.com.pl/2006/09/23/install-your-hp-laserjet-1020-on-ubuntu/)
Thanks again jrussoz and alshurooqi, hope this may be of help to some-one out there :D

---

