---
title: "New driver for ATI Radeon 9600"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by umdzig on 2005-07-29
Im trying to install a new video driver and dont know which one to choose.

When i type
"sudo apt-get install fglrx-driver"

It then asks me to choose between

xfree86-driver-fglrx 4.3.0-8.8.25-0ubuntu11
&
xorg-driver-fglrx 6.8.0-8.8.25-0ubuntu11

I have an ati radeon 9600 on my inspiron 8600. Should i use the xfree or xorg driver?

Also once i do install the driver will this cause problems to the extent that i will only have access to the command line? only asking cause it seems a few people have gotten the same problem.

---

### Post by amohanty on 2005-07-30
Hoary uses xorg so go with the scond one if you have hoary. Dunno abt Warty.

AM

Edit: to configure use:
>> fglrxconfig

this will create/mod the /etc/X11/xorg.conf

AM

---

### Post by umdzig on 2005-07-30
k thx, it works!

---

