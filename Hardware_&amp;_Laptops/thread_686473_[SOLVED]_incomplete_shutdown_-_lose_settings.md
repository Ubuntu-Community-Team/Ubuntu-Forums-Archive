---
title: "[SOLVED] incomplete shutdown - lose settings"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by Dr. Cox on 2008-02-03
hi there,

i've searched similar threads but can't find a solution for my problem.
I'm using ubuntu 7.10 on an acer tm290 laptop.  my new install went flawlessly. all apps are working reasonably ok. BUT

whenever i try to shutdown my laptop

1) screen blackens
2) cannot restart x 
3) power and wifi and any other light of the laptop is still on
4) i have to power it off with the main switch / removing battery

5) on restart i always have to reconfigure evolution and my firefox bookmarks. :shock:

can anyone help me? :confused:

cheers

---

### Post by Dr. Cox on 2008-02-03
found this:

[http://www.togaware.com/linux/survivor/APM_Power.html](http://www.togaware.com/linux/survivor/APM_Power.html)

then realized, that apm in ubuntu seems to be a module.

so:
add the following line to /etc/modules:



  apm power_off=1

worked for me!

---

