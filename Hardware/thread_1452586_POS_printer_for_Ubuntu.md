---
title: "POS printer for Ubuntu"
date: 2010-04-12
forum: Hardware
---

### Post by boondocks on 2010-04-12
I am looking for a Point of sale (POS) Printer that:
[LIST]
[*]Is used for printing receipts.
[*]Works with Ubuntu.
[/LIST]

What would you recommend?

---

### Post by lonelydragon757 on 2010-06-05
I was curious if you have found a solution yet...
I would assume that majority of them should be compatible with
linux in general...  Working for one of the major companys that is
in the point of sale business.  I have understood some of the concepts
but the software is a bit more advanced than I can actually understand
for my own personal desires...  

But what I have learned.  MOST of the manufactures should be using OPOS
or JPOS or whatever technology.. which is all open source.  and how I understand
it and could be completely WRONG...  

is that these are almost DRIVERLESS drivers...  meaning... cross platform type
of way of communicating with any POS peripheral.  And when I could find Epson 
drivers for WINDOWS...  but not for NCR printers... could only find the OPOS stuff.
which I have YET to understand how to utilize.  but realize all the printing was going
thru THAT and not windows itself even though the printer I was using was on the
windows platform...

so, my theory... it should be cross platform, with that OPOS/JPOS/ stuff... which is 
a universal, standardization of using POS equipment.  but how to use it... I have no
clue...

I hope that helps and if you figure out. I hope you can tell me!

---

### Post by boondocks on 2010-06-05
The Star Micronics TSP100U is supposed to work with Ubuntu, according to the resellers and their tech support.
I have not yet tried it myself.
See these PDFs:
[http://www.starmicronics.com/Download/Marketing_Materials/TSP100U_Spec.pdf](http://www.starmicronics.com/Download/Marketing_Materials/TSP100U_Spec.pdf)
[http://www.starmicronics.com/Download/Marketing_Materials/TSP100U_Brochure.pdf](http://www.starmicronics.com/Download/Marketing_Materials/TSP100U_Brochure.pdf)

---

### Post by MicahCarrick on 2010-11-03
I'm building myself a little POS system for my company. It's Python and GTK+ running on Ubuntu 10.10.

For the printer, I went with the USB version of a Star TSP-650 Thermal Receipt Printer. I had to build the manufacturer provided drivers since for my system (AMD64) but it was quite painless. Works great. Here are my notes:

_[Star TSP600 Series Printers in Ubuntu Linux]("http://www.micahcarrick.com/star-tsp650-tsp651-printer-ubuntu-linux.html")_

If you haven't already taken care of this piece yet, I also got a MagTek USB Swipe Reader working for credit cards:

_[MagTek Credit Card Reader in Linux]("http://www.micahcarrick.com/credit-card-reader-pyusb.html")_

---

### Post by suomaf on 2010-12-06
Could I ask the reason why you decided to write your own? What are the options that are available for Ubuntu. Thanks for any advise.

---

