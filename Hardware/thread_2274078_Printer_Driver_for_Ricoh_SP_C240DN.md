---
title: "Printer Driver for Ricoh SP C240DN"
date: 2015-04-17
forum: Hardware
---

### Post by justnpeace on 2015-04-17
Hello Gurus,

I am new to Ubuntu/Linux (actually not quite, but have been using it actively). Recently trying out Ubuntu 14.04 for office usage which, obviously, require printing function.

Setup:
1) Network connected printer Ricoh SP C240DN

Result of driver installation:
1) Automatically directed to Ricoh Aficio SP C222SF as recommended printer driver.
- but it does not work
- The printing is sent, the "Data In" light on the printer flashes, then the file /var/log/cups/access_log says Print OK
but nothing more happens
- Also tried Ricoh SP C340DN driver but in vain.

Would appreciate if anyone could give assistance.

Thank you in advance.


Cleers.

---

### Post by bapoumba on 2015-04-18
I wont be able to help you with this particular printer, but I have used the Linux OpenPrinting drivers with some success for a different model. Things I could not use are setting a password to print and some extra options (punching holes for ex).

[http://www.openprinting.org/printer/Ricoh/Ricoh-Aficio_SP_C420DN](http://www.openprinting.org/printer/Ricoh/Ricoh-Aficio_SP_C420DN)
[https://wiki.linuxfoundation.org/en/OpenPrinting/Database/RicohFAQ](https://wiki.linuxfoundation.org/en/OpenPrinting/Database/RicohFAQ)
[http://unix.stackexchange.com/questions/46004/printing-problems-with-ddst-aka-pcl6-printer-ricoh-aficio-sp-c240dn](http://unix.stackexchange.com/questions/46004/printing-problems-with-ddst-aka-pcl6-printer-ricoh-aficio-sp-c240dn)
[http://unix.stackexchange.com/questions/58719/ricoh-aficio-sp-100su-e](http://unix.stackexchange.com/questions/58719/ricoh-aficio-sp-100su-e)

But :
[http://sourceforge.net/p/gimp-print/mailman/gimp-print-devel/thread/alpine.LNX.2.00.1304231618180.4511@nelson.suse.de/](http://sourceforge.net/p/gimp-print/mailman/gimp-print-devel/thread/alpine.LNX.2.00.1304231618180.4511@nelson.suse.de/)

---

### Post by davidvandoren on 2015-04-18
I had a similar problem with a Ricoh printer I think model 2045
I went to the settings and changed the drive from recommended to the cups driver and generic 2 or there was another ricoh driver available.  
Sorry I don't remember, but I changed the driver from recommend to something else. 

Works perfectly.

---

