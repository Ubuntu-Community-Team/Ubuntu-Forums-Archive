---
title: "Problem with printing - EPSON STYLUS COLOR 300"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by peter07 on 2005-06-20
I have a big problem with my printer. It is Epson Stylus Color 300. First of all I' ve installed it with standard drivers ( which is recommended) - stcolor. 	Printouts were bad. The quality was awful and printer was stopping many times for serval seconds. 
I' ve tried second driver: stc300. The quality of printouts is better, but printer still work s slowly. In the begining it has many stops in printing. Later it works faster ( second page of the documents ect.). What may couses the stops ???

---

### Post by David Haas on 2005-06-20
Hi peter07--I can't tell you why it stops or prints poorly, but can suggest some simple things to try to correct the problem. I've found that when one selects and undesirable PPD file, it's best to delete the recognized printer from the Gnome printer manager and begin over by selecting "New Printer". Then select your printer and then the driver (the PPD file). Sometimes it's best to turn on the printer before booting Ubuntu. I see that Ubuntu Hoary has 3 PPD files for the Epson Stylus Color 300, all in the Epson directory in foomatic-ppds at /usr/share/cups/model/foomatic-ppds/Epson. These are Epson-Stylus_Color_300-stc300.upp.ppd.gz
Epson-Stylus_Color_300-stcany.upp.ppd.gz
Epson-Stylus_Color_300-stcolor.ppd.gz

You could easily try the one you haven't tried yet. 

I'd make sure that you have selected (in the print manager GUI) the correct paper size. Are you using letter or A4?

David

---

### Post by peter07 on 2005-06-21
Thank you for your advise,

When I was reinstalling my printer i noticed that I had selected bad port ( Cannon is default). I chose good port and I installed stc300 driver. Now everything works great.

---

