---
title: "Minolta PagePro 1350W Laser Printer not working"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by KYAAngel on 2005-06-23
Has anyone gotten this printer to work under hoary?  It does not detect it automatically which is not surprising after reading the authors notes on the driver.  I manually set it to USB #1 and a few other ones randomly and sucessfully installed the driver but no connection seems to have been made.  I was under the impression that USB should work and that is really how I would like it setup.  Sending test pages to the priner just results in a "no connection".
Any ideas?

---

### Post by David Haas on 2005-06-23
KYAAngel--I've not had any experience with Minolta printers and I didn't get a positive search result for this brand in the Forum. Some members have reported that their printer needs to be on before booting, and I found this to be true for my former Epson. So, I'd at least try this, if you haven't already. What PPD file did you choose? Ubuntu has supplied one, I see, in the Minolta directory at /usr/share/cups/model/foomatic-ppds/Minolta. It's Minolta-PagePro_1350W-min12xxw.ppd.gz. When selected, you should have an unzipped copy at /etc/cups/ppd. Did you set up the printer in the Gnome printer manager? If you did this without success, you might try installing it on the command line: lpadmin -p name -v device -m model. I've not had to do this, but I think "name" would be "Minolta" (without the quotes), "device" would be "usb:/dev/usb/lp0" and "model" would be the PPD file name. Perhaps Ubuntu doesn't have the correct dependencies. You could see whether these are listed at the Minolta Web site.
Well, perhaps these ideas will be of some help.
David

---

### Post by Inv on 2006-02-07
I've also been having this same problem. Has anyone had any luck?

---

### Post by Wyando on 2006-03-03
The following link will give a solution:

[http://www.linuxprinting.org/forums.cgi?group=linuxprinting.minolta.general;article=569](http://www.linuxprinting.org/forums.cgi?group=linuxprinting.minolta.general;article=569)

 I've tried it with a minolta PagePro1200W and it works.

Wyando

---

### Post by Redandtheblue on 2007-08-19
Hello, does anyone know where this link points.  I installed the driver and installed the ppd in Cups.  However the 1350w does not get recognized in CUPS.  Any help would be greatly appreciated.  I am on the verge of buying a different printer.

---

### Post by Redandtheblue on 2007-08-19
scratch that I got it to work. a restart did it. I think it may be due to the printer not being on when I first plugged in

---

