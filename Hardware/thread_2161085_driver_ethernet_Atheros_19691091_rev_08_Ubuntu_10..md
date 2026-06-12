---
title: "driver ethernet Atheros 1969:1091 rev 08 Ubuntu 10.04 LTS"
date: 2013-07-09
forum: Hardware
---

### Post by santeLibra on 2013-07-09
Good morning to all,





 
 
 I use Ubuntu 10.04 LTS for a few months but I'm not very good in the installation and compilation of modules and kernel. Should I use Ubuntu 10.04 LTS on a desktop PC that uses an ethernet network card 






Atheros Communication Device 1969:1091 rev 08 but 
lsmod : no ethernet module is loaded

 Following the info on different sites and also ubuntu forums I was able to compile and install the compat-drivers-2013-03-04-u.tar.bz2, as a result I got
ls /lib/modules -R : alx.ko module installed
lsmod : no ethernet module is loaded

Someone can help me? Thank you very much .

---

### Post by sanderj on 2013-07-09
Questions:

Why are you using 10.04? If it's the Desktop version, it's not supported anymore

What happens if you live-boot 12.04.2 LTS and/or 13.04? Does the ethernet card work then?

---

### Post by santeLibra on 2013-07-10
I use the usb stick for several pc, if I change version of ubuntu might create compatibility problems with the software I use. Switching to 12.04 or 13.04 I think it would solve, but I would spend a bit of time to resolve with 10.4 version

---

### Post by sanderj on 2013-07-10
> **santeLibra said:**
> I use the usb stick for several pc, if I change version of ubuntu might create compatibility problems with the software I use. 

Which software?

Easy step: get another USB stick, put 12.04.2 LTS on it, start using it.

---

