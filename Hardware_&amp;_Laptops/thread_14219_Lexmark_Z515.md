---
title: "Lexmark Z515"
date: 2005-02-05
forum: Hardware &amp; Laptops
---

### Post by digital_k on 2005-02-05
OK after an hour googling trying to solve my printer problem, I was able to run down a driver, lexmark z600. However, being a newbie more or less to linux, the directions I came across say to use alien to convert the package to debian and then install? Can someone tell me exactly how I would do this? Any help appreciated and thanks in advance.......

---

### Post by digital_k on 2005-02-06
[COLOR=Red]**Anyone???**[/COLOR] 8-[

---

### Post by subjectdenied on 2005-02-06
hi,
  
   ```
alien -d packagename.rpm
``` 
  
  converts the packagename.rpm to debian package. after this run
  
   ```
dpkg -i generated_deb.deb
``` 
  
  for installing the generated_deb.deb
  
  hope it helps!

---

### Post by digital_k on 2005-02-06
I was able to get the package converted, however when I try the install script, it says that archive or directory can't be found? And the icon for the new .deb package has a padlock on it. I tried this a million times, and it still won't install..lol...Anymore help appreciated.

---

### Post by Fugee on 2005-06-20
[QUOTE=digital_k]I was able to get the package converted, however when I try the install script, it says that archive or directory can't be found? And the icon for the new .deb package has a padlock on it. I tried this a million times, and it still won't install..lol...Anymore help appreciated.[/QUOTE]
What package did u download and where did you get? I have the same printer and am very interested in getting it to work.

---

### Post by jetcomputer on 2006-04-12
You can do this....

download the driver here: [http://www.downloaddelivery.com/srfi...S-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfi...S-1.0-1.TAR.gz)

Copy and paste this on a window Terminal

tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
tail -n +143 z600cups-1.0-1.gz.sh
tar -xvzf install.tar.gz
alien -t z600cups-1.0-1.i386.rpm
alien -t z600llpddk-2.0-1.i386.rpm
sudo tar xvzf z600llpddk-2.0.tgz -C /
sudo tar xvzf z600cups-1.0.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
/etc/rc2.d/S19cupsys restart
cd /usr/lib/cups/backend
./z600

Restart the computer and go to system, administration, printing, add printer, and select lexmark lexmark z510 series, click next and then select (on model) z600 v1.0-1 then click apply and you ready to go. Restart maybe needed.

---

