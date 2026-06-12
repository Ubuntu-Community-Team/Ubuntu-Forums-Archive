---
title: "Printing Full Page"
date: 2015-03-22
forum: Hardware
---

### Post by Lori_Imel on 2015-03-22
I have an Epson 1430 printer.  I finally figured out how to get the drivers etc for it....  So it is printing, but not how I want to have it print....

I have 12x12 inch papers that I want to print full on US Paper size.  In Windows, thru the image viewer in Explorer - I would print it as a full sheet.  SO it would fill up the whole page (printing a part of the paper/image)....  How can I do this in Ubuntu?

Also, is there something that explains all of the advanced settings - or a tutorial on getting the best image printed?  The colors are off, so I am sure I need to tweak some of the settings - ie photoshop quality.  My printer is a professional photographic printer - I want to use it to the best of its ability!

Thank you

---

### Post by pdc on 2015-03-22
so if I was looking for a driver for an Epson 1430: (I see there is one called Artisan; and another called Stylus by Epson;)

I would go here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and type in 1430 and I would get [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule) and I think I would go for the full feature driver so I would end up here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16715&DSCCHK=fa2dfa70c618c51b10e20f61b82e616f96a8a40e](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16715&DSCCHK=fa2dfa70c618c51b10e20f61b82e616f96a8a40e) and I would download for a 32bit system the [COLOR="#008000"]epson-inkjet-printer-201114w_1.0.0-1lsb3.2_i386.deb[/COLOR] or for a 64bit the [COLOR="#008000"]epson-inkjet-printer-201114w_1.0.0-1lsb3.2_amd64.deb
[/COLOR]
____________-

is that what you did please? If you copied this command ```
dpkg -l | grep epson-inkjet-printer
``` into a terminal; and then copied the result; and pasted it back here please; that would be very helpful

_____________

some folks might elect to print a large photograph from within GiMP ............. but one should be able to set printer options from with the menu/administration/printing icon by right-clicking on the Epson entry

---

### Post by Lori_Imel on 2015-03-23
I installed the driver thru system settings (not the terminal).  It was the 201114w.....

When I copy that code, I get nothing...


Too get a larger printed imaga - I even tried choosing larger paper.... but that did not work either....

---

### Post by Vladlenin5000 on 2015-03-23
You must have the wrong driver because you couldn't have installed it via system settings. The latest Ubuntu has native drivers for a few Epson Artisan models but not for 1430.
Choosing other model will certainly not work or at best result in what you're experiencing.

Post #2 has everything you need to install the correct (proprietary??) driver according to the manufacturer.
Delete the printer you already have and follow the instructions provide in post #2.

---

### Post by Lori_Imel on 2015-03-23
> **pdc said:**
> so if I was looking for a driver for an Epson 1430: (I see there is one called Artisan; and another called Stylus by Epson;)

I would go here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and type in 1430 and I would get [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule) and I think I would go for the full feature driver so I would end up here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16715&DSCCHK=fa2dfa70c618c51b10e20f61b82e616f96a8a40e](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=16715&DSCCHK=fa2dfa70c618c51b10e20f61b82e616f96a8a40e) and I would download for a 32bit system the [COLOR=#008000]epson-inkjet-printer-201114w_1.0.0-1lsb3.2_i386.deb[/COLOR] or for a 64bit the [COLOR=#008000]epson-inkjet-printer-201114w_1.0.0-1lsb3.2_amd64.deb
[/COLOR]_____________

some folks might elect to print a large photograph from within GiMP ............. but one should be able to set printer options from with the menu/administration/printing icon by right-clicking on the Epson entry

I finally got it to download - site was acting funky.....  Now what do I do?   I have not done too much in the terminal this time around.  Is the software center that reliable for using?  I am having issues with it crashing....

---

### Post by Lori_Imel on 2015-03-23
I forgot what I originally did....  I set up the printer via CUPS.....  I just did that again... but it did not ask for a driver....  I did have to select it as the 1400 - nothing for the 1430 (which is the replacement model for the 1400),,,,

---

### Post by Vladlenin5000 on 2015-03-23
Have you installed the driver already?
Yes, you can open it and install with Software Center. It's just a frontend.

---

### Post by Lori_Imel on 2015-03-23
I figured out how to do this in the terminal....  here is the result...

dpkg -l | grep epson-inkjet-printer

ii  epson-inkjet-printer-201114w                          1.0.0-1lsb3.2                                       amd64        EPSON Artisan 1430 Series - Epson Inkjet Printer Driver

---

### Post by Vladlenin5000 on 2015-03-23
Now you should have a new entry, specifically for 1430 at system settings > printers.
That one should work as well as (or almost) the Windows driver.

---

### Post by Lori_Imel on 2015-03-23
I did figure out how to get the full page print - I put it into LibreOffice Writer....  :)  

I need to work on the colors though - I have a blue jean texture - and it does not print out very blue.... more green than blue.....  

Thank you

---

### Post by pdc on 2015-03-24
Vladlenin5000 has done a great job guiding you; 

looks like you got the Epson driver installed; 

If you right-click on the icon for this driver; that is in the PRINTERS box in the menu ............ there should be options to tweak colours??

Other options are printing images through GIMP; and tweaking colours there; and for those that prize very special images, they install the turboprint driver: [http://www.turboprint.info/](http://www.turboprint.info/) these folks put food on their table by working on quality drivers to support a large range of printers; we have used it and it gives very good images; it costs the equivalent of a few beers; I have seen some very pleased punters who have chosen to install turboprint

---

### Post by Lori_Imel on 2015-03-24
Earlier, I was having problems with my colors not printing.... So I deleted my printer in cups.... and started over.... lo and behold - the 1st item list actually was the 1430.   Wow what a difference it made.  My blue jean texture is actually BLUE!!!

---

### Post by pdc on 2015-03-24
good work; if you feel things are approaching the SOLVED state, as owner of the thread (you are the owner?) ............. you can edit THREAD TOOLS (top-right) and enter SOLVED

---

### Post by Lori_Imel on 2015-03-25
> **Lori_Imel said:**
> I have an Epson 1430 printer.  I finally figured out how to get the drivers etc for it....  So it is printing, but not how I want to have it print....

I have 12x12 inch papers that I want to print full on US Paper size.  In Windows, thru the image viewer in Explorer - I would print it as a full sheet.  SO it would fill up the whole page (printing a part of the paper/image)....  How can I do this in Ubuntu?
Thank you

I was going to close this.... but the 1st part of my questions still applies....

I thought I was doing this in LibreOffice Writer....  I was putting my square texture into a page and then dragging it's edges to fill up the page.  Last night, I discovered when I had a texture with more of a design, that it was distorting it, not keeping it proportional.  I am a digital scrapbook designer - I design scrapbook papers that I want to print out to use in my projects.  I design 12x12 papers, but print out a portion of that onto letter size paper.  

Any ideas on how I can get this done?

Thank you! :)

---

### Post by pdc on 2015-03-25
best always to seek out those regularly doing stuff

If you go here [http://libreofficeforum.org/](http://libreofficeforum.org/) to the libreoffice forum, that is surely the best chance of getting help

---

