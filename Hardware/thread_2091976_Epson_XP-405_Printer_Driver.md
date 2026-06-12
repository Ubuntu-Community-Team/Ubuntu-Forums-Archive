---
title: "Epson XP-405 Printer Driver"
date: 2012-12-06
forum: Hardware
---

### Post by Tav1 on 2012-12-06
Hello everyone.

I have recently purchased an Epson XP-405 printer and stupidly forgot to see if it was compatible with Ubuntu. I know most of you will be annoyed with me and blame me for this error but if we can put that aside, is there a driver anywhere that I could download to allow this printer to work on Ubuntu 12.04? 

I have tried searching it in Google, but no luck. Have even chatted to the Epson team and they have given me some useless links that were meant to direct me to a driver but there are no drivers for the XP-405. Does anyone know where there is a driver download for this printer?

Thank you for your time.

---

### Post by pdc on 2012-12-06
this is the link to look for linux drivers for Epson

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

....it's the Epson site ..if I type in 405 I get

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

and I follow the top line I get

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18786&DSCCHK=9b896a8ce134b9e9ed63ba6bf8190361ee56e412](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18786&DSCCHK=9b896a8ce134b9e9ed63ba6bf8190361ee56e412)

as ubuntu uses debian packages, you need the .deb packages

.....you don't say if you have 32bit or 64bit

obviously the ..

[COLOR="SeaGreen"]epson-inkjet-printer-201203j_1.0.0-1lsb3.2_amd64.deb[/COLOR] is for 64 bit ..

and 

[COLOR="SeaGreen"]epson-inkjet-printer-201203j_1.0.0-1lsb3.2_i386.deb[/COLOR] is for 32bit

........as you click to download, gdebi installer is likely to leap in and offer to install for you.....I would accept this kind offer..thus the printer driver should be installed and all ready to go ........

________________________________________________________________

SCANNER COMPONENT


[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20233&DSCCHK=e8c8d6c7f9da68399277d5eddbf8121aecda09d5](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20233&DSCCHK=e8c8d6c7f9da68399277d5eddbf8121aecda09d5)

this page has the scanner bits.........*[COLOR="DarkOrchid"]find the accept button to click to display them[/COLOR]* ......

You need bottom of the page ......... [COLOR="SeaGreen"]**iscan-data_1.19.0-1_all.deb**[/COLOR] first..I say again.. you need [COLOR="SeaGreen"]**iscan-data_1.19.0-1_all.deb**[/COLOR] first..

......let gdebi installer do its work ......

then 

choose the correct deb package depending on 32bit or 64bit

you will need either 

iscan_2.29.1-5~usb0.1.[COLOR="Blue"]ltdl7[/COLOR]_amd64.deb

or 

iscan_2.29.1-5~usb0.1.[COLOR="Blue"]ltdl7[/COLOR]_i386.deb

as [COLOR="Magenta"]ltd3[/COLOR] is for earlier linux kernels............

---

### Post by Tav1 on 2012-12-07
You are a star! Well done. =D The problem was that I was typing in  "XP-405" into the Epson Drivers search instead of "405". Thank you so  much for your help and detailed answer.

---

### Post by pdc on 2012-12-07
delighted it all worked for you; ..............scanner going too?           enjoy :D

---

### Post by munkee on 2012-12-08
I have been looking at buying this printer.  Did you get it scanning and printing with your wi-fi or you used a USB connection?  Many thanks.

---

### Post by Ubuntist on 2013-04-17
> **pdc said:**
> this is the link to look for linux drivers for Epson ....

Thanks, pdc -- I've installed my new XP-405 under Quantal, and it works great as a printer, both wirelessly and through a USB cable.

As for scanning, it works over the USB cable but not yet wirelessly.  For one thing, the printer can't seem to find my computer, but I'm working on that.

There was on little bump along the way, which I'll mention just in case somebody else encounters it.  Following Epson's instructions, I ran:

```

sudo dpkg --install iscan-data_1.22.0-1_all.deb
sudo dpkg --install iscan_2.29.1-5~usb0.1.ltdl7_amd64.dep

```

The first time I did this, I got an error message about xsltproc not being installed.  I opened the Ubuntu Software Centre, which told me it was already installed, so I tried again, and this time the dpkg commands worked fine.  Maybe there was some kind of delayed installation issue.

---

### Post by Ubuntist on 2013-06-16
Allow me to update my experience with using the XP-405 under 13.04 Quantal.

The problems I had initially with wireless scanning seem to have vanished now that I have installed Epson's basic Linux driver instead of the super-duper ultra-fancy version.  If I'm missing anything by using the basic driver, I haven't noticed it.

---

