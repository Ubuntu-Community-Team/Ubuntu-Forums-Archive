---
title: "hot to install printer driver for canon pixma mp780"
date: 2006-05-18
forum: Hardware &amp; Laptops
---

### Post by cliveau on 2006-05-18
please send me a printer driver for **canon pixma mp 780**. thank you

---

### Post by bswilson on 2006-05-18
There isn't one that I could locate.  However, I installed a driver package from this Web site, which offers a pretty slick tool for adding support for printers.  I personally have a PIXMA MP760, and I used the closest driver I could find, which was for the MP750.  Worked like a charm!

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

---

### Post by cliveau on 2006-05-29
[QUOTE=bswilson]There isn't one that I could locate.  However, I installed a driver package from this Web site, which offers a pretty slick tool for adding support for printers.  I personally have a PIXMA MP760, and I used the closest driver I could find, which was for the MP750.  Worked like a charm!

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)[/QUOTE]


thank you very much bs wilson. the links help a lot

---

### Post by jdpipe on 2006-08-14
Hi all

There seems to be some talk on the net about free/unrestricted linux drivers for this printer (Canon Pixma MP760). Check out here:

[http://www.techbuilder.org/recipes/167600449](http://www.techbuilder.org/recipes/167600449)

I'm hoping that converting these RPMs with Alien will allow the drivers to work fine. Note also that this page

[http://gentoo-wiki.com/Canon_pixma_series](http://gentoo-wiki.com/Canon_pixma_series)

gives some info on which driver should be right for which model. It says that the bjfilter-pixusip4100 driver is the right one for the Pixma MP760 -- or at least *should* be.

Cheers
JP

---

### Post by jdpipe on 2006-08-14
For the record, note also that the 'free' version of TurboPrint is pretty much useless: it places big logos in the middle of your printed pages. Be aware that you must pay 30 USD to get a 'personal use' license before you can usefully employ TurboPrint. This is not clear from their website.

JP

---

### Post by robertmcox on 2006-08-20
FWIW, I tried the pixusip4100 drivers and they seemed to work marginally.  I had to change the paper size and the colors weren't quite right on my MP-780.  The driver wouldn't honor my choice for paper tray.  ](*,) 

Reluctantly, I paid turboprint.de and I'm glad I did.  The turboprint software works great!  It remembers my settings, allows duplex, lets me choose the paper tray, and even configures CUPS printer sharing automagically.  I was printing across the network (2 x Ubuntu 6.06) in less than 2 minutes!

Be sure to send a harassing e-mail to Canon like I did (I even got a reply, but no promises) asking for linux support.  [-( 

Also to mention, the scanning function works using this open-source driver:

[http://home.arcor.de/wittawat/pixma/](http://home.arcor.de/wittawat/pixma/)

---

### Post by mesci on 2006-09-04
Does anyone know if the turbo print drivers cover all aspects of the pixma (scanning and faxing) or just printing?

---

### Post by gttocs on 2006-10-07
> **jdpipe said:**
> For the record, note also that the 'free' version of TurboPrint is pretty much useless: it places big logos in the middle of your printed pages. Be aware that you must pay 30 USD to get a 'personal use' license before you can usefully employ TurboPrint. This is not clear from their website.

JP

Not entirely true.  I noticed that if you set the quality to "Draft", it will not print the logo.  It defaulted to "Medium" and therefore printed the logo on my first test.  Use the xtpconfig command to see all the options and change the quality.  

I may register anyway, it is a slick tool.  It supports all my printers and supports lots of options in the registered version.    I guess until manufacturers start making Linux drivers, something like this is necessary.  I sent an email to Canon, everybody should contact their printer manufacturer and request Linux drivers.

---

### Post by gttocs on 2006-10-07
> **mesci said:**
> Does anyone know if the turbo print drivers cover all aspects of the pixma (scanning and faxing) or just printing?

Just printing.

---

### Post by brickbat on 2006-10-18
There is a scanner driver now too.

[http://home.arcor.de/wittawat/pixma/](http://home.arcor.de/wittawat/pixma/)

---

### Post by brundles on 2006-11-20
I'm looking at getting a direct CD/DVD printer like the MP780. Do the TurboPrint drivers give you the ability to be able to use the direct disc printing?

Thanks!

---

### Post by brickbat on 2006-11-20
Yes they do but it was such a pain to get going that I gave up and used windows for printing to cd's.  You have to set this and set that and don't forget to stand on your right leg and wiggle your left index finger. :D

---

