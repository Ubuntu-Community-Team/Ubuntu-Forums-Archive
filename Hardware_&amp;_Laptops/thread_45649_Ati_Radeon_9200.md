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

### Post by somez on 2005-07-01
> **alper_tr]my laptop that uses ati radeon 9200 as well. Even everything seems to work fine. I think ubuntu is not using it up to its limits. And when i checked it said:**
> www.mesa3d.org[/url]
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


I am new to linux. Thus I wonder how would improve the performance or install a new driver and configure. Or if anyone already installed drivers for ati radeon 9200; i might consider using his\her lines for my Xorg.conf file.

Thanks already;

System:
Compaq presario x1030us Laptop
1.4 Centrino
ATI RADEON 9200
512 MB Ram

You must go to /lib/modules/fglrx/build_mod an exectue the make.sh script, by typing sh make.sh as root user. After this you must go to /lib/modules/fglrx and execute make_install.sh. Now it should work, restart your X server with ctrl+alt+backspace and run fglrxinfo again. You should now see ATI technologies... text.

Ah yeah, to explain your problem. The problem was that the ATI driver was using software rendering, but with the new modules we just built, opengl is working too. Good luck!

---

### Post by alper_tr on 2005-07-02
there is no such folder there as you suggested...
now what i do ?

---

### Post by Stemp on 2005-07-02
Use the new driver's installer from the ati site  ;-)

---

