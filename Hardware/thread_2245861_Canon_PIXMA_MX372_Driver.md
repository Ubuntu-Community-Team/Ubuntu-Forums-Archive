---
title: "Canon PIXMA MX372 Driver"
date: 2014-09-26
forum: Hardware
---

### Post by bigbankclub on 2014-09-26
I need to locate a driver that will work with my Canon PIXMA MX372 - Could not find a thing online. Any suggestions for a generic driver? It see's the printer and it does not recognize any of the requests done for a print. Unless I'm missing the boat - please help.

---

### Post by weatherman2 on 2014-09-26
Try the driver for the MX375, available on Canon's Europe site (probably Asia too).  Search the web for "pixma mx375 europe."  You'll want the Debian package, not the RPM version.

---

### Post by pdc on 2014-09-27
Hi bigbankclub

as weatherman says, Canon do provide drivers;

if you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100412401.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100412401.html?r=s&q=) and click to download, and select SAVE you will get [COLOR="#008000"]cnijfilter-mx370series-3.70-1-deb.tar.gz[/COLOR]

_______________________________

before install though, you need [COLOR="#0000FF"]libtiff4[/COLOR] and get it from here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/)

......... go 14 or so down the list and select the 32bit or 64bit (only you know which of them you have installed);

_______________________________

after that, if you open a terminal; and paste in the commands below, **line by line**; hit the **ENTER** key after each paste ..........

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mx370series-3.70-1-deb.tar.gz
cd cnijfilter-mx370series-3.70-1-deb
./install.sh[/COLOR]

and that will start the install script;

---

