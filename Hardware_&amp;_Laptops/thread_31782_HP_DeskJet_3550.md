---
title: "HP DeskJet 3550"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by snowx1000 on 2005-05-04
Most applications print fine, however OpenOffice seems to only be able to print in landscape regardless of the settings I modify. Does anyone know of a solution for this. Thank you.

---

### Post by DutchLau on 2005-05-04
Hi snowx1000

Try following this "HowTo" I made a while back:

I've just installed my HP 5150C Deskjet with Ubuntu. It seems to work well - but only AFTER I got the official drivers installed from HP. Perhaps this has something to do with the printer driver not being supported by cups. I'm an uber noob with Linux so I've warned you. If you inflict any damage upon your PC it's not my fault!

Take a look at this website by HP. [http://hpinkjet.sourceforge.net/productssupported.php](http://hpinkjet.sourceforge.net/productssupported.php) and see which type of driver is best for your printer. Search for your HP model.

Now go to [http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi) Download the .PPD file for YOUR printer.

Now we'll go to Gnome and we'll set up your printer. Go to System => Administration => Printing. Add a New printer, follow the steps (Use detected printer) Choose the model, Press "Install Driver" and find the .PPD file you saved. 

This should successfully install the printer. Restart cups, or reboot the computer, either works.

Let us know if it worked!

Cheers,

DutchLau

---

### Post by snowx1000 on 2005-05-05
Thanks for the help, but still no luck. It says I need to use HPILP, but that requires ubuntu-desktop to be uninstalled, which I dont really want to do. I will try some other things, please let me know if you have other suggestions. Thanks.

---

### Post by snowx1000 on 2005-05-06
It turns out that the page properties for the particular document I was trying to print in openoffice were set to landscape. All is well now :-)

---

### Post by jodef on 2005-05-06
[QUOTE=snowx1000]It turns out that the page properties for the particular document I was trying to print in openoffice were set to landscape. All is well now :-)[/QUOTE]I am glad to hear everything works I have the same model printer so your success is my success. :)

---

### Post by DutchLau on 2005-05-07
[QUOTE=jodef] your success is my success. :)[/QUOTE]

Come again?  :razz: 

DutchLau

---

