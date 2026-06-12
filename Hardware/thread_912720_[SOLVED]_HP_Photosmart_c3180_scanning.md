---
title: "[SOLVED] HP Photosmart c3180 scanning"
date: 2008-09-07
forum: Hardware
---

### Post by masterhyun on 2008-09-07
Hi, all
I have all-in-one HP Photosmart c3180.
I can print, but I don't know how can I use the scan function.
My system is Ubuntu 8.04 the Hardy Heron.
Does anyone know how can I scan?

---

### Post by coffeecat on 2008-09-07
The OpenPrinting page [for your machine]("http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C3180_All-in-One") gives some useful information about the printer, but according to the [sane-project page]("http://www.sane-project.org/cgi-bin/driver.pl?manu=HP&model=C3180&bus=any&v=&p=") the scanner is unsupported.

Having said that, the sane-project website looks a bit neglected so that information may or may not be up-to-date. What happens when you go to Applications > Graphics > Xsane Image Scanner with the machine plugged in and switched on?

---

### Post by Sef on 2008-09-07
> I have all-in-one HP Photosmart c3180.
I can print, but I don't know how can I use the scan function.

1) Try Coffeecat's idea.  That should work.

2) Have you downloaded HPLIP Toolbox from Add/Remove?  If not, then Applications > Add/Remove > Search: HPLIP > check box next to HPLIP Toolbox > click apply changes > click apply > close.

---

### Post by masterhyun on 2008-09-09
> **coffeecat said:**
> The OpenPrinting page [for your machine]("http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C3180_All-in-One") gives some useful information about the printer, but according to the [sane-project page]("http://www.sane-project.org/cgi-bin/driver.pl?manu=HP&model=C3180&bus=any&v=&p=") the scanner is unsupported.

Having said that, the sane-project website looks a bit neglected so that information may or may not be up-to-date. What happens when you go to Applications > Graphics > Xsane Image Scanner with the machine plugged in and switched on?



Thanks a lot. With Xsane Image Scanner it simply works. Awesome.

---

### Post by masterhyun on 2008-09-09
Thanks for both coffeecat and sef. 
It simply works with Xsane.
Thank you guys. :-)

---

### Post by Sef on 2008-09-09
> Thanks for both coffeecat and sef. 
It simply works with Xsane.
Thank you guys

Thank you for letting us know that the solution worked.

---

### Post by thermalCat on 2012-05-04
boom. works in mint 12 too

---

