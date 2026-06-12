---
title: "Acer 8104 Wireless button LED"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by ano1 on 2006-06-04
Hi,

I am trying to get all the wireless functionality of my new Acer 8104 laptop to work. On the front of my laptop there is a Bluetooth and a Wireless button both with LEDs that light them up. 

The bluetooth button's LED turns on and off when pressed though I have yet to figure out how to see if it acutally disable and enable bluetooth. But I digress. 

I am trying to get the Wireless button to light up and activate/deactivate my wireless connection.  Any help would be greatly appreciated.

JAS

---

### Post by mihai.ile on 2006-06-04
As i explained here about my laptop (acer) had the same problem:
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1694WLMi](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1694WLMi)

to solve this my solution (tested on 2 different acer's) was:
> 
To make wireless front led work I just open/created(if does not exist) this file:

~$ sudo gedit /etc/modprobe.d/ipw2200 

and add this line:

options ipw2200 led=1 

and after restart the led worked just fine.

---

### Post by ano1 on 2006-06-04
[QUOTE=mihai007]As i explained here about my laptop (acer) had the same problem:
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1694WLMi](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1694WLMi)

to solve this my solution (tested on 2 different acer's) was:[/QUOTE]

Thanks that worked perfectly.

JAS

---

### Post by constitutionrules on 2006-07-18
Bumb for information I will need

---

