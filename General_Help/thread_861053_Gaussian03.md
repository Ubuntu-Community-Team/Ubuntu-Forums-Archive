---
title: "Gaussian03"
date: 2008-07-16
forum: General Help
---

### Post by susruta101 on 2008-07-16
I am using Gaussian03 with Ubuntu 8.04. g03 runs fine but while I try to run Gaussview, it has some problem. It says [COLOR="Red"]/usr/local/gv/gview: symbol lookup error: /usr/local/gv/lib/libqt-mt_sc.so.3: undefined symbol: XftPatternCreate[/COLOR]
By the way this Gaussview is installed in /usr/local/gv
What to do for this problem???

---

### Post by susruta101 on 2008-08-18
After installing the library files, Gaussview is running but there is graphics problem. The screen is black with lots of colourful stripes. If I click on the workspace, the window is activated and I can see whatever I have drawn but in 1sec it goes again.

---

### Post by hjbolide on 2008-10-04
install xft-lib or something

---

### Post by dufm04 on 2009-01-11
Hi. I had the same problem during the installation of Gaussview....But I resolved it installing libxft1 library, which is an old ubuntu lib. The link is: [http://packages.ubuntu.com/dapper/libxft1](http://packages.ubuntu.com/dapper/libxft1). Download it, install it using GDebi and that is all, you will have running Gaussview!!

I hope help you!!!

**PD: All credits to [http://senabre.myphotos.cc/cgi-bin/blosxom/2008/02/28](http://senabre.myphotos.cc/cgi-bin/blosxom/2008/02/28) (is in spanish).**

---

