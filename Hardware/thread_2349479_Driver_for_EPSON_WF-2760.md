---
title: "Driver for EPSON WF-2760"
date: 2017-01-15
forum: Hardware
---

### Post by epeedk on 2017-01-15
Has anyone found a driver for EPSON WF-2760, or gotten it to work in other ways? 
I am running Kubuntu 16.10.

---

### Post by pdc on 2017-01-15
If you go here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX), (the Epson download centre); and enter WF-2760, it offers you drivers for scanning and printer; I would suggest you download the **[COLOR="#008000"]Epson Printer Utility[/COLOR]** as the fuller driver

you don't mention if you have 64bit, but assuming you do, you would be downloading **[COLOR="#008000"]epson-printer-utility_1.0.0-1lsb3.2_amd64.deb[/COLOR]** which is a debian package: are you happy to install debian packages on your system: 

to run the scanner, it takes you to this page [http://support.epson.net/linux/en/imagescanv3.php?version=1.1.14](http://support.epson.net/linux/en/imagescanv3.php?version=1.1.14) where you specify what you need

let us know how it all goes

---

### Post by epeedk on 2017-01-16
Found the package I needed to install:
[FONT=monospace][COLOR=#000000]sudo apt-get install printer-driver-escpr[/COLOR]
[/FONT]

---

