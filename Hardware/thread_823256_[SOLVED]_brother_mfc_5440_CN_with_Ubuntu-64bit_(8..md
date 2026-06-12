---
title: "[SOLVED] brother mfc 5440 CN with Ubuntu-64bit (8.04 Hardy)"
date: 2008-06-09
forum: Hardware
---

### Post by HorstJENS on 2008-06-09
Hi, does anyone managed to get a **brother mfc 5440 cn** all-in-one printer working together with a 64-bit version of Ubuntu 8.04 hardy ?

Brother provides .deb packages and a faq how to adapt those drivers to the 64-bit version of ubuntu 7.10
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142)

However even if i do all those steps from the faq i get a "wrong architecture" message when trying to install the .deb packages.

I was able to work with this printer and ubuntu 7.10 (32-bit version). The printer is connected via network, not via USB.

-Horst

---

### Post by HorstJENS on 2008-06-09
thanks to the German forum [www.ubuntuusers.de](www.ubuntuusers.de) i found a solution:

installing the packages brother-cups-wrapper-extra and brother-lpr-drivers-extra via synaptic.

i can print now (again) :-)

-Horst

---

### Post by rbringh on 2008-08-18
Well this one worked for me with a MFC-420CN. Just acquire the material using synaptic. It does the install. Once the install is completed just add the printer as usual. Nothing else worked for me on my 64 bit AMD system.

---

### Post by blheste61 on 2009-09-23
I am new to Ubuntu, and I am trying to get my MFC5440cn working on my new 9.04 install.  Does anyone have the necessary driver files for this printer model?  The download from the Brother support site does not appear to be working for this model anymore. :confused:
 
Thanks.

---

