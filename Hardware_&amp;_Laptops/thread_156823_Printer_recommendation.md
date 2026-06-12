---
title: "Printer recommendation"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by adrian_m on 2006-04-07
I'm looking into buying a new printer.
I would like one of those multi-function printers, that's also a scanner, copier, (maybe also fax), but I want it to be a network printer, that I can plug in to my ethernet hub or switch and have it be available to all my computers on my network.

I've seen several regular printers that can do this, but what I want is a multifunction one. So that I can not only print but also use the scanner over the network from any of my my computers. I would like to have this feature compatible with Linux, Windows and Mac OS X.  I don't think I've ever seen a multifunction printer that advertises this feature being compatible with all three OSs.

Does anyone have any experiences with this or know of one?

---

### Post by dreamsINdigital on 2006-04-07
I'm not sure about that feature you want being compatible on all platforms, but HP's line of multi-function printers are great; check those out.

---

### Post by Sef on 2006-04-07
Epson or HP printers are the best for Linux.  I have an HP PSC 1610 and it works very well.

Check out this site for more info:

[http://www.linuxprinting.org]("http://www.linuxprinting.org")

---

### Post by mcf1986 on 2006-04-12
just dont get a lexmark... im going through hell trying to get it to work.

---

### Post by alinux on 2006-04-12
If you Get Samsung ml-1610 Laser Monochromatic:

HOWTO:
Samsung ML-1610 Installation on Ubuntu Breezy ML-1610


1.Donwload Samsung ML-1610 driver from:

[http://www.samsung.com/support/productsupport/download/Model_Select.aspx?type=Printer&typecode=300500&subtype=Laser+Printer&subtypecode=300501&model=ML-1610&filetype=DR&language=](http://www.samsung.com/support/productsupport/download/Model_Select.aspx?type=Printer&typecode=300500&subtype=Laser+Printer&subtypecode=300501&model=ML-1610&filetype=DR&language=)

2.Extract the archive somewhere you can get at it.


3.Use the package manager to fetch libgtk 1.2 
(to prevent problems, use the root terminal!)

sudo apt-get install libgtk1.2-common

4.Then:

sudo adduser cupsys shadow

5.Restart cupsys:

sudo /etc/init.d/cupsys restart

6.Type: sudo passwd root [sets up a temporary root password]

7.Go to wherever you extracted the drivers and type: ./setup.sh

8. Follow the prompts. If all goes well you should end up in Samsung's setup utility. 
If you somehow don't get there, typing linux-config in a terminal will get you there.

9."Add printer"

10.Enter the root password you created in step 7

11.Follow the prompts; I can't help you here, these settings depend on your actual setup

12.When you're all done, type: sudo passwd -l root [disables root password]

13.Your printer should be configured and available in System -> Administration -> Printing.

---

### Post by mips on 2006-04-12
HP 6213 or 6210

---

### Post by StratosL on 2006-04-14
[QUOTE=mips]HP 6213 or 6210[/QUOTE]

Does this work as a printer only or as a printer - scanner - fax?

Thanks, 

Stratos

---

### Post by mips on 2006-04-14
The printer & scanner works 100%. The fax works as a stand-alone fax machine. I honestly dont know whether the fax functionality is suppose to work in any other way as I have never read up on it. I can receive and send faxes from the multifunction device but never tried from the PC or know whether it is a supported function or not (irrespective of OS)

---

