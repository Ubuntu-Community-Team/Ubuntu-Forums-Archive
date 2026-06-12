---
title: "HP Deskjet 3525 on Lubuntu"
date: 2013-03-20
forum: Hardware
---

### Post by Venidle on 2013-03-20
Hello everyone,

This is my first post and i'm not really experienced with Linux, please keep it in mind ;)

I'm trying to install new printer (HP Deskjet 3525) on Lubuntu 11.10 oneiric. I successfully added printer, everything seemed to work fine but it was not printing actually. I installed hplip, but when typing hp-info -i it says: error: No device selected/specified or that supports this functionality.

I also found this: [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) but I don't understand some stuff. 

I have no idea what to do, please help!

---

### Post by Rex Bouwense on 2013-03-20
HP printers are very Linux friendly.  Is the printer that you have an HP Deskjet Ink Advantage 3525 E-all-in-one?  I just went to the HP web site and that printer is supported.  There is an install wizard that will guide you through the process of installation.  
[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)
It sounds like the installation did not go well.

---

### Post by Venidle on 2013-03-23
Thank you, Rex Bouvense, for responding. 

Yes, that's the very printer.

This is what I get on printer's error log: [COLOR=#000000]Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf. And this is what the guide shows: [/COLOR]Ubuntu 12.04 supplies HPLIP 3.12.2 and it does not support your printer. 

[edit] 

Printer works fine (thank you very much, i think it was sth with hplip), but during some jobs it reports system errors and during installation it showed a warning about gnome-keyring (no such file or directory).

---

### Post by Rex Bouwense on 2013-03-23
Glad that you got it working.  As I said HP, is very Linux friendly and their install wizard is one of the best.

---

