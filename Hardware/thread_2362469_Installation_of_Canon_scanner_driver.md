---
title: "Installation of Canon scanner driver"
date: 2017-05-29
forum: Hardware
---

### Post by alex-bingham on 2017-05-29
Been away from Ubuntu for a while and I am having a noobie moment.  I have downloaded a scanner driver from the Canon website, unpackaged it and for the life of me I can't remember how to install the driver.  Apologies for the numpty question but can somebody just point me in the right direction?

Thanks

Beaker Boy

---

### Post by kc1di on 2017-05-29
Hello Alex-bingham - Welcome Back to Ubuntu.
A Few questions first.  Have you tried setting up the printer with the print manager?  Which Cannon scanner/printer? and which version of Ubuntu.
All this will help tell you what to do. Most scanners in later versions of Ubuntu are supported out of the box.  Have you tried using simple Scan?

---

### Post by alex-bingham on 2017-05-29
Canon MG 7500 on Ubuntu 16.04.  When I open Simple Scan it doesn't see the scanner

Sorry, and yes the printer is connected and works

---

### Post by slickymaster on 2017-05-29
*Thread moved to **Hardware**.*

---

### Post by kc1di on 2017-05-29
[This page]("http://tipsonubuntu.com/2016/08/14/canon-printer-driver-scangear-mp-ubuntu-16-04/") may be of help -- It seems from what I can find you need the mp scanner software from cannon

---

### Post by vasa1 on 2017-05-29
> **alex-bingham said:**
> ... downloaded a scanner driver from the Canon website ...
What is the exact link you used?

---

### Post by pdc on 2017-05-29
so to get ScanGearMP that Canon provide; if you went here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100627102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100627102.html) and clicked to download and SAVE  you would get scangearmp2-3.00-1-deb.tar.gz


If you open a terminal; and paste in the commands below; line by line; hitting the ENTER key after each paste ......

```
cd Downloads
tar -xzvf scangearmp2-3.00-1-deb.tar.gz
cd scangearmp2-3.00-1-deb
```

then comes the install script
 ```
./install.sh    
```           and it will ask you for your sudo password

....... to run ScanGearMP, ```
scangearmp2
``` in a terminal and you then set up a launcher to ... launch it ..............

---

