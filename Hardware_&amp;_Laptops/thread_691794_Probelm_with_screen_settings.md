---
title: "Probelm with screen settings"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by shlomi_bt on 2008-02-09
Hi to you all,
  I've installed ubuntu 7.10 on my laptop (ibm t61) using virtual box.
  during the instalation and runtime i recieved a message which told me to change the colurs to 32 bit.
  my pc is set for that and the resolution is 1440*900.
  
  how do i set the ubuntu display to work properly-i cannot increase the resolution bigger than 800*600.
thanks.
  shlomi.

---

### Post by Yellow Pasque on 2008-02-09
Run this to configure your screen with the intel driver (unless you have the optional nvidia graphics card).
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Also, here's a helpful site for your laptop:
[http://www.thinkwiki.org/wiki/Category:T61](http://www.thinkwiki.org/wiki/Category:T61)

---

### Post by shlomi_bt on 2008-02-09
...thanks, and if i have the nvidia card...what shell i do?

---

### Post by Yellow Pasque on 2008-02-09
If you have the nvidia card, you'll need to install the nvidia proprietary drivers, in which case  you should look into a program called Envy. More than likely, you have the integrated Intel graphics. To find out which card you have:
```
sudo update-pciids; lspci | grep VGA
```

---

