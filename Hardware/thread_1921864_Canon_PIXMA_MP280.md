---
title: "Canon PIXMA MP280"
date: 2012-02-07
forum: Hardware
---

### Post by darbiniece on 2012-02-07
Hi!

I have this problem, that I can't connect my Canon Pixma MP280 printer nor scanner to Ubuntu 11.10. I've downloaded drivers from here [http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP280.aspx?type=download&page=1](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP280.aspx?type=download&page=1)
even tried to install them, but still some drivers are required.
I'm new to Ubuntu, so basically I need some advices what to do and how.

Thanks already!

---

### Post by marin123 on 2012-02-07
No need for printer drivers, they are already in kernel.

Your printer should be plug 'n' print. What kind of error do you get?

---

### Post by darbiniece on 2012-02-08
usr/lib/cups/filter/pstocanonij (i've googled this, but find nothing that would help)
something like this is required and it doesn't print. Also scanner is not recognized.
yeah, but I think that there were not drivers for this printer in kernel.

Maybe there is some way i can use drivers which are in install CD? I've tried this, but nothing happened. Just files.

---

### Post by marin123 on 2012-02-08
I had similar problems with my printer (MP240). Can you copy-paste exactly what error do you get?
The drivers from your CD are useless. Can you also say what exactly did you do with printers you downloaded from Canon website?

---

### Post by darbiniece on 2012-02-09
[https://answers.launchpad.net/ubuntu/+source/cups/+question/175575](https://answers.launchpad.net/ubuntu/+source/cups/+question/175575)
I did these steps.
/usr/lib/cups/filter/pstocanonij" not available: No such file or directory
and this is the error which I get.
and as scanner it's not recognized at all.

---

### Post by ElGaton on 2012-02-09
It's better to use the PPA provided by Michael Gruz. Just uninstall the current Canon driver and follow the instructions on this page:
[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)
Your model (MP280) is not explicitly listed on the page - the correct package names are "cnijfilter-mp280series" and "scangearmp-mp280series".

The instructions given there apply to any modern Canon printer.

---

### Post by Linux Dutchman on 2012-02-09
> **marin123 said:**
> No need for printer drivers, they are already in kernel.
 
Your printer should be plug 'n' print. What kind of error do you get?
 
Canon devices are not always supported out-of-the-box by the Linux kernel. 
 
@darbiniece: 
Check here for an how-to:
[https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers](https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers)

---

### Post by darbiniece on 2012-02-12
Everything went okay, but in the end it was just written:
Unable to locate package cnijfilter-mp280series
is it possible that there is no such package?

---

### Post by PapaGary on 2012-02-12
> **darbiniece said:**
> Everything went okay, but in the end it was just written:
Unable to locate package cnijfilter-mp280series
is it possible that there is no such package?
It appears so.

---

### Post by darbiniece on 2012-02-14
So it means I can't install this particular printer?

---

### Post by marin123 on 2012-02-15
I have Michael Gruz PPA on my laptop and it has your driver.

Did you add the PPA to your computer?
Did you update package list? (sudo apt-get update)
Did you install your driver? (sudo apt-get install cnijfilter-mp280series)

You can open Synaptic and search for "cnijfilter". Your printer's name should be on the list, mark the package for installation and click apply.

---

### Post by darbiniece on 2012-02-19
Yay. I managed to set printer. Thanks a lot!
but scanner still isn't recognized.

---

### Post by marin123 on 2012-02-19
> **darbiniece said:**
> Yay. I managed to set printer. Thanks a lot!
but scanner still isn't recognized.

Did you open Simple Scan? My MP240 works out of the box. Just connect it with USB and scan.

---

### Post by darbiniece on 2012-02-19
Yes I did but it can't find scanner. Also I tried to install scanner driver again, but it's already installed. I don't get why is this so.

---

