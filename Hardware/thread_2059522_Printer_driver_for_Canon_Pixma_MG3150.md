---
title: "Printer driver for Canon Pixma MG3150"
date: 2012-09-18
forum: Hardware
---

### Post by Johnread on 2012-09-18
I need a printer driver for the Canon Pixma MG3150 in Xubuntu 12.04. Can anyone provide one or give a link to where one is to be found ?

---

### Post by pdc on 2012-09-18
go here

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MG3170&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MG3170&menu=download&filter=0&tagname=g_os&g_os=Linux)

this is the linux page for the Canon 3100 series of printers;

ubuntu uses .deb packages;

............so you need 

1) MG3100 series IJ Printer Driver Ver. 3.60 for Linux (debian Packagearchive)

.....this is to get the printer component running

click to download; or double-click; gdebi installer will likely offer to install for you; I think the 3150 has a wireless option; I have a similar printer; I just opted for the usb connection as the install started; 

*I think Canon suggest leaving the printer off; till the prompt on the screen during install says to turn the printer on*................

2) Scanner

Canon provide a separate programme called ScanGear that runs their scanners

download the .deb package for this

MG3100 series ScanGear MP Ver. 1.80 for Linux (debian Packagearchive)

again, gdebi installer is likely to jump in and offer to install; let it;

to run this programme, copy and paste into a terminal; or type

> scangearmp

.........to save you doing that each time, create a launcher...............I note you have xubuntu.......google on > create launcher xubuntu 12.04......for further references

[http://www.ubuntubuzz.com/2011/12/install-and-configure-slingshot.html](http://www.ubuntubuzz.com/2011/12/install-and-configure-slingshot.html)

if you subscribe to a thread, (top right..........thread tools.......you can keep in touch more easily...................)

---

### Post by aikishugyo on 2012-09-19
Gutenprint 5.2.9 also has support for the MG3100 series. It seems Ubuntu 12.04 only has gutenprint 5.2.8-pre1, which was a pre-release for MacOSX users for debugging purposes. 5.2.8 was released after 6 months of bug-fixing, and because there appeared a packaging error, 5.2.9 was released shortly thereafter.
I sincerely hope 5.2.9 gets into Ubuntu repos soon, else users could install it locally (it does not clash with system installation, as it goes in /usr/local).
Regards,
Gernot Hassenpflug

---

### Post by birkopf on 2013-04-12
How do you make this (quite mad) printer to work on wifi with ubuntu 12.04 ? I actually have Zorin 6 but it's fully based on Ubuntu 12.04. 
I can't install this driver as error comes saying that system doesn't see the printer. This happens on cable and wifi installation. 

On cable printer works on default ubuntu options, but no matter what I would do - I can't get it to be discovered by wifi. 


Help please ?

---

