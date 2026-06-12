---
title: "Epson XP-410 WIFI installed but no print nor scan"
date: 2015-03-23
forum: Hardware
---

### Post by rafael29 on 2015-03-23
Hi. After some research, I was finally able to install my Epson XP-410 Wifi printer.  I can see it in the menu, but when I try to print or scan, I just get a message that it can´t connect to the printer at all.  I have tried everything, even installed other drivers, but it still won´t connect to printer when printing.  Is there a step by step guide on how to setup, connect and test the printer so it prints?

---

### Post by Tsepo_Joshua on 2015-03-24
sudo apt-get install lsb

then open a terminal where you have the deb, i'll guess your Downloads/
cd ~/Downloads
sudo dpkg -i epson-inkjet-printer-escpr_1.4.4-1lsb3.2_amd64.deb
or if your not running a 64 bit install:
sudo dpkg -i epson-inkjet-printer-escpr_1.4.4-1lsb3.2_i386.deb

now just use the printer manager to add the printer it will find the drivers you just installed.

---

### Post by pdc on 2015-03-24
so Tsepo_Joshua has very kindly pointed out the drivers you need; I am not clear from your post that you have those in your Downloads folder; so for anyone else coming after, one would go here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and type in 410 

and that takes you to here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=22524&DSCCHK=be2881cd731a22e340ed2e96eb71ee0725faab96](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=22524&DSCCHK=be2881cd731a22e340ed2e96eb71ee0725faab96) and this shows the full feature drivers; [COLOR="#008000"]epson-inkjet-printer-201303w_1.0.0-1lsb3.2_i386.deb[/COLOR]	 and [COLOR="#008000"]epson-inkjet-printer-201303w_1.0.0-1lsb3.2_amd64.deb[/COLOR] ..............the driver [COLOR="#EE82EE"]epson-inkjet-printer-escpr_1.4.4-1lsb3.2_amd64.deb[/COLOR] is what I think Epson call the [COLOR="#EE82EE"]generic driver[/COLOR]: the one I mention above should have more features:

to set up a printer; you need to do 3 things in this order:

1) establish the connection
2) install the drivers
3) register the printer on your system

_________

1) is it wireless? If so, you need to have it accepted by your router before proceeding ............Epson have information videos that guide to enter the password for your router; or use the WPS method

2) driver install as above

3) Epson don't provide an install script; (Canon and Brother do); so for Epson you need to ADD  A NEW PRINTER through the PRINTER box in the ubuntu menu

---

