---
title: "install print driver/update cups"
date: 2008-08-16
forum: General Help
---

### Post by KenSpeedie on 2008-08-16
I need to load a print driver (Epson Stylus CX9400Fax).

I downloaded gutenprint-5.1.7.  When I compiled it (./configure) everything went as planned except it says it did not "build cups".  I am assuming that means it did not update the cups database.  

After installing gutenprint I used System->Administration->Printer.  It recognized my printer, but the driver did not show up in the database.

Sourceforge website says that my printer is included in the latest gutenprint.

How do I get it to update the cups database while it is compiling?

Thanks for your help.

Ken

---

### Post by Naatan on 2008-08-16
What printer are you using?

I've never used gutenprint.. cups + printer driver always worked for me.. that being said I've never had any problem finding the driver and I'd love to see if I can find your driver.

---

### Post by KenSpeedie on 2008-08-17
I am trying to find the driver for an Epson Stylus CX9400Fax.

Everything I find lists through CX8400.

I am begining the think that this printer is too new.

I can't find a ppd file for this printer.  gutenprint-5.0.2 says it has the driver for the CX9400, but when I install it the CX9400 does not appear in the database.

Could be I don't know how to install this driver? (If I can find it).

Thanks for your help

---

### Post by Naatan on 2008-08-17
It appears gutenprint is already installed in Hardy (package name: cupsys-driver-gutenprint).

You might want to try using a driver of a printer with a version number as close as possible to the one you have.. I've done this before and had my printer working flawlessly.

---

### Post by KenSpeedie on 2008-08-17
Naatan:

None of the drivers listed in the printer database work with my printer.

Does anybody know how often and when Ubuntu will update their gutenprint database?

Thanks for your input.

Ken

---

### Post by Dr Small on 2008-09-15
I also have a Epson Stylus CX9400Fax. Openprinting.org database lists the Driver:
[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX9400Fax](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX9400Fax)

I have CUPS running, and downloaded and installed the gutenprint x86 32bit DEB for LSB 3.1, installed it with dpkg, and then went back into the CUPS web interface, added the printer, but the CX9400 driver is not there. Why is that?

If I could get this printer working, then my parent's will switch to Ubuntu. But in the meantime...

Anyone have any suggestions? I would really like to get this working!

Dr Small

---

