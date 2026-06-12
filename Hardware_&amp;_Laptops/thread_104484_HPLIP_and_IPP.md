---
title: "HPLIP and IPP"
date: 2005-12-16
forum: Hardware &amp; Laptops
---

### Post by eeclark on 2005-12-16
I found out what the problem is with IPP and HPLIP.

When you enter a URI during the creation of the printer, it appears all well and good. For example, if you put in hp:/net/psc_2500_series?ip=192.168.1.97 in the IPP field, it will appear as you typed it. BUT IF YOU SAVE YOUR CHANGES (click close) and then GO BACK to view the connection properties, ipp:// is now inserted in front of the hp:/ .

In other words, when I create a printer and enter the URI...the system wants to insert a prefix of ipp:// in front of hp:/

I guess the thing to do is to find out what is generating the "ipp://" and take that out...but that is beyond me.

Any response is appreciated.

Thanks.

Edward Clark

---

### Post by eeclark on 2005-12-16
I also noticed that if the printer is created in the CUPS interface ([http://localhost:631](http://localhost:631)) you do not see the problem of autopopulating IPP.

It only happens in the gnome-cups-manager.

---

