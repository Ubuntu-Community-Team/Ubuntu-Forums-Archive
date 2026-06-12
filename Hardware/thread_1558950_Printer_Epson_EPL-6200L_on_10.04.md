---
title: "Printer Epson EPL-6200L on 10.04"
date: 2010-08-22
forum: Hardware
---

### Post by six648 on 2010-08-22
10.04 can detect Epson EPL-6200L, but not work, 

so I downloaded ghostscript_8.14-2_i386.deb from
[http://sourceforge.net/projects/epsonepl/files/](http://sourceforge.net/projects/epsonepl/files/)

```
$ sudo dpkg -i ghostscript_8.14-2_i386.deb
dpkg: warning: downgrading ghostscript from 8.71.dfsg.1-0ubuntu5.2 to 8.14-2.
...
dpkg: error processing ghostscript_8.14-2_i386.deb (--install):
 conflicting packages - not installing ghostscript
```

---

### Post by IcarusR on 2010-08-23
Have you tried uninstalling version 8.71.dfsg.1-0ubuntu5.2 first then install  8.14-2.
Once you get it installed & working you will need to pin it at that version otherwise newer version will be reinstalled.

---

### Post by ellgor on 2010-08-23
Hi, 

If your still having problems try this site "Avasys" its for Epsons, also if you have a scanner, while your on the download page at "Avasys" scroll right down till you see an app called "Imagescan.deb" get that as a must, its competely seperate from the main package.

Regards, Ellgor.

---

### Post by six648 on 2010-08-23
Epson Epl-6200L works now. 

#download "epsonepl" driver from 
[http://sourceforge.net/projects/epsonepl/files/](http://sourceforge.net/projects/epsonepl/files/)
(Version 0.4.1 (current) worked in my case)

```
cd /usr/src
sudo tar zxvf  /<download-place>/epsoneplijs-0.4.1.tgz
cd epsoneplijs-0.4.1/
sudo ./configure
sudo make
sudo make install
sudo mkdir -p /usr/share/cups/model/foomatic-ppds/Epson/
sudo cp -av ../foomatic_PPDs/Epson-EPL-*-cups.ppd.gz   /usr/share/cups/model/foomatic-ppds/Epson/
sudo cp foomatic/driver/epl6200l.xml    /usr/share/foomatic/db/source/driver/
sudo cp foomatic/opt/epsonepl-*   /usr/share/foomatic/db/source/opt/
sudo  cp foomatic/printer/Epson-EPL-6200L.xml  /usr/share/foomatic/db/source/printer/
sudo /etc/init.d/cups restart
```#delete the previous detected printer and add a new printer EPL-6200L in
sysytem> Administration >printing

---
modified the source from
[http://ubuntuforums.org/showthread.php?t=901529&highlight=epl6200L](http://ubuntuforums.org/showthread.php?t=901529&highlight=epl6200L)

---

### Post by edwarr on 2011-05-25
Hi, 

Just a note. Got it working using the above on a clean 11.04.
Had to add a final 

#sudo cp ijs_server_epsonepl /usr/bin/

Many thanks,

E

---

### Post by javacookies on 2011-09-12
anyone got for 64 bit?
I have Ubuntu 11.04 and it detected my printer and installed EPL-6200 driver..not 6200L and It's not working,any help? thanks :)

---

### Post by Peter2009 on 2011-12-03
> **edwarr said:**
> Hi, 

Just a note. Got it working using the above on a clean 11.04.
Had to add a final 

#sudo cp ijs_server_epsonepl /usr/bin/

Many thanks,

E

I did need to do this part on 10.04 2.6.32-36-generic, otherwise I get an error message
But nicely done! well done! keep up the good work! ;-)

---

