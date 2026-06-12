---
title: "Lexmark Z515"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by Fugee on 2005-06-28
Has anyone gotten a Z515 to work on Ubuntu? I've found several different threads which have mentioned the printer, but none ever have a resolution. I've looked at LinuxPrinting and LinuxQuestions, but nothing on Ubuntu. Found a nice HOWTO for Gentoo, but once again of little help to me.

---

### Post by Fugee on 2005-06-30
[QUOTE=Fugee]Has anyone gotten a Z515 to work on Ubuntu? I've found several different threads which have mentioned the printer, but none ever have a resolution. I've looked at LinuxPrinting and LinuxQuestions, but nothing on Ubuntu. Found a nice HOWTO for Gentoo, but once again of little help to me.[/QUOTE]
 bump

---

### Post by jetcomputer on 2006-04-12
You can do this....

download the driver here: [http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz)

Copy and paste this on a window Terminal

tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz 
tail -n +143 z600cups-1.0-1.gz.sh 
tar -xvzf install.tar.gz 
alien -t z600cups-1.0-1.i386.rpm 
alien -t z600llpddk-2.0-1.i386.rpm 
sudo tar xvzf  z600llpddk-2.0.tgz -C / 
sudo tar xvzf z600cups-1.0.tgz -C / 
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
/etc/rc2.d/S19cupsys restart
cd /usr/lib/cups/backend
./z600

Restart the computer and go to system, administration, printing, add printer, and select lexmark lexmark z510 series, click next and then select (on model) z600 v1.0-1 then click apply and you ready to go. Restart maybe needed.

---

### Post by ripperzane on 2008-03-12
By doing the bolded, I had success
> **jetcomputer said:**
> You can do this....

download the driver here: [http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz)

Copy and paste this on a window Terminal

tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz 
tail -n +143 z600cups-1.0-1.gz.sh_** >> install.tar.gz**_
tar -xvzf install.tar.gz 
alien -t z600cups-1.0-1.i386.rpm 
alien -t z600llpddk-2.0-1.i386.rpm 
sudo tar xvzf  z600llpddk-2.0.tgz -C / 
sudo tar xvzf z600cups-1.0.tgz -C / 
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
/etc/rc2.d/S19cupsys restart
cd /usr/lib/cups/backend
./z600

Restart the computer and go to system, administration, printing, add printer, and select lexmark lexmark z510 series, click next and then select (on model) z600 v1.0-1 then click apply and you ready to go. Restart maybe needed.

---

