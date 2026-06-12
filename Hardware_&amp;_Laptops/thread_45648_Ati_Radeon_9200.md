---
title: "Ati Radeon 9200"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by alper_tr on 2005-07-01
my laptop that uses ati radeon 9200 as well. Even everything seems to work fine. I think ubuntu is not using it up to its limits. And when i checked it; even the system recognisez it as ati radeon 9000,

When i do fglrxinfo over terminal, it says:
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


I am new to linux. Thus I wonder how would improve the performance or install a new driver and configure. Or if anyone already installed drivers for ati radeon 9200; i might consider using his\her lines for my Xorg.conf file.

Thanks already;

System:
Compaq presario x1030us Laptop
1.4 Centrino
ATI RADEON 9200
512 MB Ram

---

### Post by Juergen on 2005-07-01
I have no ati-cards, but synaptic says the drivers provide hardware accelerated OpenGL
So IMHO you shouldn't have Mesa but 'ATI somthing' as OpenGL vendor.

Open a terminal and type 'sudo dpkg-reconfigure xserver-xorg', you should get an option for the fglrx-driver.

---

