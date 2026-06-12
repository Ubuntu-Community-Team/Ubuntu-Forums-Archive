---
title: "Problems with colours on various printers"
date: 2017-10-04
forum: Hardware
---

### Post by desconocido on 2017-10-04
In May I installed Ubuntu Mate 16.04 on my Toshiba laptop.

I installed software for my Epson Stylus SX420W with:

```
GDebi epson-inkjet-printer-nx420_1.0.0-1lsb3.2_amd64.deb 
Run cups 2.1.3 by browsing to localhost:631
Adding Printers and Classes -> Add Printer -> Discovered Network Printers -> Epson Stylus SX420W (without MAC address suffix) etc..

```
The Printer Test Page on plain paper for this was fine (possibly the red had just a touch too much yellow in it).

During the summer holidays I took my laptop with me and installed various printer drivers at different places:

¶ 17-July-2017
Use cups to install driver for WiFi printer HP Deskjet 3050A
(but yellow comes out as dirty mustard colour, the cyan and magenta also come out darker than normal, the RGB are also of course darkened, the grey scale steps are darker than normal and the black is a very good black (better than my Epson black))

¶ 22-July-2017
Use USB cable to connect to Canon MG6800 printer; system automatically installs CUPS+Gutenprint driver
(but yellow comes out as dirty mustard colour etc (as the HP above))
This is not a problem for other computers using the printer.

¶ 28-July-2017
Use USB cable to connect to Canon Pixma ip3500 printer; system automatically installs CUPS+Gutenprint driver:
colours OK

Later, back home again using the Epson Stylus SX420W:
colours OK

Any ideas?

---

### Post by slickymaster on 2017-10-04
Thread moved to **Hardware** for a better fit

---

### Post by desconocido on 2017-10-04
This thread
[https://askubuntu.com/questions/708702/canon-printer-color-printing-too-dark]("https://askubuntu.com/questions/708702/canon-printer-color-printing-too-dark")
suggests that the problem is with Gutenprint - (workaround is select Color Model CMYK)

However,  this probably does not apply to the HP printer (which I think is using HPLIP).

---

### Post by desconocido on 2017-10-09
Just in case I didn't make it clear, the colours are wildly out in the two cases I highlighted. When I say "dirty mustard" I'm talking about French Dijon mustard, not British yellow mustard!

I enclose a couple of scans, made with default settings, of correct and incorrect Printer Test Pages. The scan doesn't show the colours as printed of course, but it shows the magnitude of the problem.

First, correct:
[ATTACH=CONFIG]277052[/ATTACH]

Second, incorrect:
[ATTACH=CONFIG]277053[/ATTACH]

---

