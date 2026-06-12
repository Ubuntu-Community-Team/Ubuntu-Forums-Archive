---
title: "creative web cam live"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by frrobert on 2007-01-20
I have a creative web camera live.  I installed EasyCam2 and ran the installation it found my web cam and everything seemed to be installed.  When I run camorama it says device not found.  Any ideas where to go from here?

Thanks

---

### Post by frrobert on 2007-01-26
bump

---

### Post by frrobert on 2007-01-30
Found the driver to for Creative Live Web Cam

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

for kernel up from 2.6.11 : gspcav1-20070110.tar.gz

There is a web page for opensource drivers for Creative products

[http://opensource.creative.com/](http://opensource.creative.com/)

---

### Post by Arwen on 2007-07-15
I don't want to open a new thread so I continue here..
I downloaded gspcav1-20070110.tar.gz,unzipped but what's the sudo command to make it work?
Thanx!

---

### Post by w4ett on 2007-07-15
> **Arwen said:**
> I don't want to open a new thread so I continue here..
I downloaded gspcav1-20070110.tar.gz,unzipped but what's the sudo command to make it work?
Thanx!

Here is the definitive guide:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Arwen on 2007-07-15
I typed sudo apt-get install gspcav1-20070508 and says it doesn't find it.I'm in the same directory I unzipped it..

---

### Post by chizzt on 2007-07-20
> **Arwen said:**
> I typed sudo apt-get install gspcav1-20070508 and says it doesn't find it.I'm in the same directory I unzipped it..

try  ./gspca_build

c

---

