---
title: "Gateway MX7525 and Compiz"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by Duroon on 2007-11-27
Another ATI issue I imagine, my gateway MX7525 comes with the ATI Radeon Mobility X600 graphics card. I am trying to get desktop effects up and running. On a fresh install without the restricted driver I was getting the error message of "desktop effects could not be started". Now I have th restricted driver installed and instead I get "The composite extension is not available". So does anyone have any ideas?

---

### Post by catfishk on 2007-11-27
have you tried using the binary fglrx ATI drivers?:

 [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.11_Driver_Manually)

 these are the only way to go IMO.  once installed you can add this section to your /etc/X11/xorg.conf to enable composting:

 > Section "Extensions"
        Option          "Composite"     "1"
EndSection


---

### Post by Duroon on 2007-11-27
I will give that a try, thanks.

---

### Post by Duroon on 2007-11-27
A long process but in the end I now have desktop effects working, thanks!

---

### Post by sanitys3j on 2008-01-22
The page on that wiki is not there any more.  Mind sharing how you got the effects to work?  I'm having issues with a new install on my mx7525 too.

Thank you.

---

