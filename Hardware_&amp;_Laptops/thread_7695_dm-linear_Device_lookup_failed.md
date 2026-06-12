---
title: "dm-linear: Device lookup failed"
date: 2004-12-10
forum: Hardware &amp; Laptops
---

### Post by Call Me Ishmael on 2004-12-10
Hi, I compiled and installed on my Warty a 2.6.10-rc vanilla kernel. 
This finally solved my problems with my usbstick that wasn't mounted at al,l on 2.6.8 and 2.6.9 kernels  :)
However now I have this boot error message:

dm-linear: Device lookup failed
dm-linear: Device lookup failed
(repeated 10-20 times)

The system works pretty good, apart this errors everthing is ok.
I guess I made something weird in my .config  

Any hints?  :confused:

---

### Post by DiemonasLt on 2005-06-13
[QUOTE=Call Me Ishmael]Hi, I compiled and installed on my Warty a 2.6.10-rc vanilla kernel. 
This finally solved my problems with my usbstick that wasn't mounted at al,l on 2.6.8 and 2.6.9 kernels  :)
However now I have this boot error message:

dm-linear: Device lookup failed
dm-linear: Device lookup failed
(repeated 10-20 times)

The system works pretty good, apart this errors everthing is ok.
I guess I made something weird in my .config  

Any hints?  :confused:[/QUOTE]
 It is the problem with Enterprise Volume Management System. It seems that there is the conflict between kernel volume management utilities and EVMS. More about this problem you can read here :
[http://evms.sourceforge.net/faq.html](http://evms.sourceforge.net/faq.html)
Sorry for my english :)

---

