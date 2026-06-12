---
title: "Compaq Presario M2000 problem with ATI 200M"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by JuanC on 2005-10-30
I have an AMD 64 Turion processor. And I can't get my ATI Radeon Xpress 200M card works with fglrx.

I try to install the last 8.18.8 version of ATI drivers [https://support.ati.com/ics/support/KBAnswer.asp?questionID=1177](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1177) , with alien i transform rpm package to deb.

Install without errors , but when i type *fglrxinfo* i get :
> 
display:  :0.0      screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


---

### Post by rykel on 2006-04-09
[QUOTE=JuanC]I have an AMD 64 Turion processor. And I can't get my ATI Radeon Xpress 200M card works with fglrx.

I try to install the last 8.18.8 version of ATI drivers [https://support.ati.com/ics/support/KBAnswer.asp?questionID=1177](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1177) , with alien i transform rpm package to deb.

Install without errors , but when i type *fglrxinfo* i get :[/QUOTE]

initially i managed to install fglrx from the Universe repository and got it working by "**sudo fglrxconfig**"... but after the full system upgrade of the last 2 days, i have NOT been able to find fglrxconfig, and now i have the same problem as you.

anybody knows how to enable fglrx now?

NOTE: **aticonfig --initial** does not give any errors, but does NOT change anything... **dpkg-reconfigure xserver-xorg** with fglrx produces no GUI...   ](*,)

---

