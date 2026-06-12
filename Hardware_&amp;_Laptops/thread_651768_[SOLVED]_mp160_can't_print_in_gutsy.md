---
title: "[SOLVED] mp160 can't print in gutsy"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by donyfrosman on 2007-12-27
Hallo
before when i'm using feisty, printer and scanner both work fine but when i'm installing gutsy gibbon my printer can't work only scanner that run well 

i try this code 
```

$ sudo alien -i --scripts scangearmp-common-1.00-1.i386.rpm scangearmp-mp160-1.00-1.i386.rpm cnijfilter-common-2.70-1.i386.rpm cnijfilter-mp160-2.70-1.i386.rpm

$ sudo apt-get install libpng3

$ sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

$ sudo /etc/init.d/cupsys restart
in /usr/share/cups/model
$ sudo lpadmin -p MP160 -P canonmp160.ppd -v cnij_usb:/dev/usblp0 -E

$ sudo apt-get install libxml1

$ sudo apt-get install libgtk1.2 
```

it's work in feisty but when i try in gutsy printer can't work 

can you help me?
**thanks**

---

### Post by donyfrosman on 2007-12-28
finally i can print, there is some tips in gutsy go to **system > administration > printing** and look for the setting and device url click change button, and then gutsy will searching for the driver automatically, after that printer is ready to be use.

---

