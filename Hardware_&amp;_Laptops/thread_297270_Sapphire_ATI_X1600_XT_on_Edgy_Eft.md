---
title: "Sapphire ATI X1600 XT on Edgy Eft"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by _route66_ on 2006-11-10
I have this configuration: 
Asus M2N-E Nforce 570 Ultra - motherboard
Sapphire ATI Radeon X1600 XT 256 Mb GDDR3 - video card
AMD Athlon 64 x 2 4200+ Windsor - procesor
4 x Kingston 1 GB DDR2 Pc 4300 533 Mhz 

And I can not install the ATI drivers for this card. I tried the official ati drivers and the drivers provided by Edgy Eft and nothing, when i type "fglrxinfo" this is what i get :

X[COLOR="DarkGreen"]lib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)[/COLOR]

Please a little help, I don't want to sell my card, I love ATI :(

---

### Post by user1397 on 2006-11-10
> **_route66_ said:**
> I have this configuration: 
Asus M2N-E Nforce 570 Ultra - motherboard
Sapphire ATI Radeon X1600 XT 256 Mb GDDR3 - video card
AMD Athlon 64 x 2 4200+ Windsor - procesor
4 x Kingston 1 GB DDR2 Pc 4300 533 Mhz 

And I can not install the ATI drivers for this card. I tried the official ati drivers and the drivers provided by Edgy Eft and nothing, when i type "fglrxinfo" this is what i get :

X[COLOR=DarkGreen]lib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org]("http://www.mesa3d.org")
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)[/COLOR]

Please a little help, I don't want to sell my card, I love ATI :(hvae you tried any of the troubleshooting steps here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) ??

---

### Post by _route66_ on 2006-11-11
> **erik1397 said:**
> hvae you tried any of the troubleshooting steps here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) ??
Yes, i've done it, but still nothing. By the way, i have de 64 bit version of kubuntu, an now i'm trying with the 32 bit version. Any advices would be helpfull

---

### Post by user1397 on 2006-11-13
a good guide on this: [http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

---

### Post by kosmic on 2006-11-13
After you install the Proprietary ATI drivers you need to edit your Xorg.conf file (/etc/X11/xorg.conf) and add these in the end of the file

```

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

```

After that everything will work ;)

---

### Post by Monkey358 on 2006-11-13
I followed the guides as well, and I arrived at the same issue with Mesa, so I disabled the Composite Extension and now my X is very messed up. KDE loads but only portions of the bar on the bottom are visible, as well the menus are all transparent, and once something renders on the to screen, it doesn't go away, it's a profoundly weird effect. I had to dump to terminal to fix it.

---

