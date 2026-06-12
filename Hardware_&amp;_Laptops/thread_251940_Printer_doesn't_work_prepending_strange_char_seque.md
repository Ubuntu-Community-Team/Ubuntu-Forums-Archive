---
title: "Printer doesn't work: prepending strange char sequence."
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by red_Marvin on 2006-09-06
At home I have an Epson stylus color 850 and it prints fine ...exept that it prepends a strange character sequence on each prited page:

[b]284.4
@EJL[/b]

The sequence is unformatted so I guess it is a command sent to the printer but not recognized by the printer.
The rest of the page prints fine uness for the times it stops randomly in the middle of the printing.

Any help on resolving this matter would be appreciated, since at the moment the printer is unusable for any "official" documents...](*,)

---

### Post by raldz on 2006-09-06
as what it is shown in [LinuxPrinting.org]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Color_850") your printer is perfectly supported in Linux.. however, the recommended driver is gimp-print.. you may download the driver here:

[http://gutenprint.sourceforge.net/p_Download.php3](http://gutenprint.sourceforge.net/p_Download.php3)

untar the package and read the README file for instructions how to install.. but basically, the install will be just a series of commands like:

./configure
make
make install


if an error message appears complaining about headers or gcc.. you must install first the "build-essentials" from synaptics..

---

### Post by Sef on 2006-09-06
> if an error message appears complaining about headers or gcc.. you must install first the "build-essentials" from synaptics..

Or from the command line (GNOME):

Applications > Accessories > Terminal

sudo apt-get update

sudo aptitude install build-essential

---

### Post by red_Marvin on 2006-09-06
Compiled and done.

If I open up the printer settingsm, I can choose between stc800ih.upp (which I used before) and gutenprint. However both those were available before too, does dapper perhaps come with gutenprint available by default (but not installed)? or did I bork something up by choosing it at the dropdown menu?
---
Result: the printer still stops in the middle of printing a page now and then but the "prefixes" seem to have gone. Could the stopping be because of too little memory (in the printer or whatever)?

---

### Post by raldz on 2006-09-06
> **red_Marvin said:**
> 
Result: the printer still stops in the middle of printing a page now and then but the "prefixes" seem to have gone. Could the stopping be because of too little memory (in the printer or whatever)?

I'm not that familiar with your printer, but the only way to find out is to print a text only document, and a heavy graphics print job.. if the printer stops at the later, then it could be a memory issue..

---

### Post by red_Marvin on 2006-09-08
Well, it seems to happen randomly with both images and (formatted) text so I guess I can rule that one out...

---

