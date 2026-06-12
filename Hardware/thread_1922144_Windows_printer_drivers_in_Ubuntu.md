---
title: "Windows printer drivers in Ubuntu"
date: 2012-02-08
forum: Hardware
---

### Post by JediGrzyb on 2012-02-08
Hello,

I want to install the printer OKI C810 on my Ubuntu (it's the one we've got in the office), but there are no Linux drivers for this particular model.

Is it in any way possible to use Windows drivers to set up the printer on Ubuntu?

Please help

---

### Post by Mark Phelps on 2012-02-08
Basically -- NO.

However, you could try installing the printer using CUPS -- it supplies its own drivers.  To get to CUPS, open a browser, enter "localhost:631" (without the quotes), and when the CUPS page displays, use the menus to Add a printer.

---

### Post by JediGrzyb on 2012-02-09
Unfortunately CUPS also doesn't provide drivers for this printer. I guess I shall go on printerless...

Thanks for the info, anyway.

---

### Post by mosaic2s on 2012-02-09
As a guideline, one should buy those printers that are supported on linux or drivers are given by the vendors.

---

### Post by JediGrzyb on 2012-02-09
I came to work at an office which was already equipped with an office printer. I don't think they're going to change the printer just for one person who uses Ubuntu :P

---

### Post by oldfred on 2014-02-07
User  jtojnar suggested this:
[http://foo2hiperc.rkkda.com/](http://foo2hiperc.rkkda.com/)
for several printers
 Oki 301dn, Oki C310dn, Oki C810, Oki C3100n, Oki C3200n, Oki C3300n, Oki C3400n, Oki C5100n, Oki C5150n, Oki C5200n, Oki C5500n, Oki C5600n, Oki C5800n

---

### Post by dee7 on 2014-06-11
Looked at foo2hiperc.rkkda.com as have OKI C5100 printer and installed Xubuntu 32 bit . I've an uncomfortable feeling that this is going to have a blinding obvious answer but I can't see link to download driver foo2hiperc from this site ?

---

### Post by oldfred on 2014-06-11
Yeah, not clear until about half way down:

 wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)

---

### Post by dee7 on 2014-06-13
[http://foo2hiperc.rkkda.com/](http://foo2hiperc.rkkda.com/) yes; this link does provide all the info to download this driver BUT you do need to read the instructions carefully

---

### Post by kinemagician2 on 2014-06-15
Dear All,
I used [http://foo2hiperc.rkkda.com/](http://foo2hiperc.rkkda.com/) to install my network printer OKI511DN.  Although not specifically listed, I used the driver of OKI310DN. It works like a charm.  Read CAREFULLY the instructions.

---

### Post by HCBT on 2014-06-15
It's a bit strange that in 2014 we still can't get normal printer drivers for linux. Anyway, cool that other model drivers worked. :)

---

### Post by davidvandoren on 2014-06-15
Set up the printer and choose the driver from the list.

Choose Generic and select 
**PostScript level 1**.

or if available like in PhotoPrint
choose
Adobe 
And then select PostScript level 2.

Works most of the time for me.

Or take the driver cd and look in the macitosh driver for the PPD file then don't select the driver from the list, instead check on provide a PPD file

---

