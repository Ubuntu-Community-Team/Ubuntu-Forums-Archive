---
title: "Epson TX110 printing blank pages"
date: 2013-01-19
forum: Hardware
---

### Post by TheBigH on 2013-01-19
Test page prints perfectly, but when I try to print anything else the printer goes through all the motions of printing the document, but the pages come out blank. I've tried printing from LibreOffice, Document Viewer and gedit, all with the same result.

How do I fix this problem?

---

### Post by pdc on 2013-01-19
I wonder which printer driver you have installed; 

the various Japanese companies: Epson, Canon and Brother spend a lot of time and provide good support to linux; in all its many, many variants..

if one goes here

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

I hope it shows the printer driver and scanner driver

You don't tell us if you have 32bit or 64bit ..

..assuming 32bit one would download and install the [COLOR="SeaGreen"]epson-inkjet-printer-stylus-nx110-series_1.0.0-1lsb3.2_i386.deb[/COLOR]	

.....as you click to download, gdebi installer should leap in and offer to help: I would accept its kind offer .........

and for the scanner, 

go here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20920&DSCCHK=1f66541498e19eb24ca3c111022918affda59631](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20920&DSCCHK=1f66541498e19eb24ca3c111022918affda59631)

and download and install in this order

1) [COLOR="SeaGreen"]iscan-data_1.20.0-1_all.deb[/COLOR] .....find it at the BOTTOM of the list !!

2) [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.[COLOR="Magenta"]ltdl7[/COLOR]_i386.deb[/COLOR] (*assuming 32bit and [COLOR="Magenta"]ltd7[/COLOR] is for newer kernels*)

3) [COLOR="SeaGreen"]userg_revQ_e.pdf[/COLOR] is a how-to .............. most only read the instructions if all else fails.......you may wish to download and read it first!

---

