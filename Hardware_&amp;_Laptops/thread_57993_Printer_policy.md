---
title: "Printer policy"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by sophtpaw on 2005-08-18
Hi, 
As a newbie i need advice on how to go about getting a printer that will match my GNU/Linux Ubuntu (hoary) system.

in the printer configuration tab i see makes and models of printers. As a rule if a printer is not listed there should i not get it?
should i only get a printer whose make and model is listed?

I appreciate some advice and feedback on this issue,

--
sophtpaw

---

### Post by David Haas on 2005-08-18
sophtpaw--The following site is the standard reference for printers for Linux: <http://www.linuxprinting.org/printer_list.cgi>  Some general statements should help you in your selection. HP and Epson support Linux better than other makes. HP even supplies drivers free to the Linux community. Canon and Lexmark (Dell printers are made by Lexmark) provide poor support, and seem, from my experience with the Forum, to be hard to install. I think it's easiest to purchase a printer for which Ubuntu includes a PPD file. The PPD files are in two directories: (1):/usr/share/cups/model/gimp-print/4.2, and (2) /usr/share/cups/model/foomatic-ppds. 

When my Epson stylus C82 died, I checked the PPD files for HP in the HP diectory at /usr/share/cups/model/foomatic-ppds/HP and picked the HP Deskjet 5740, because a PPD file for it was present in Ubuntu, it was mid-level in price ($90), and it was in stock at my nearby Office Max.  It installed easily with the Gnome printer manager (System>Administration>Printing from the top taskbar) and has worked perfectly. 

I hope this gives you some orientation about printers for Ubuntu.

David

---

