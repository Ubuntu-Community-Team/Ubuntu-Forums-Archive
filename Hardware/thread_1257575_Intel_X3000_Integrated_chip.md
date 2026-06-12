---
title: "Intel X3000 Integrated chip"
date: 2009-09-04
forum: Hardware
---

### Post by gr8108 on 2009-09-04
Hi. I wanna install Xubuntu on my Gateway 3238m (specifications [here]("http://www.gateway.com.mx/support/product_support.html?cat=Desktops&subcat=GT+Series&model=GT3238m")). This PC has a integrated video chip based on Intel X3000, modified by Gateway. I tried Xubuntu LiveCD and using lshw command I observerd video driver is a generic one. When I'm using Windows, the driver provider is Gateway not Intel.
 
My question is: ¿Is there a specific driver for my PC? ¿Where can I get it?
 
Thanks a lot.

---

### Post by SoftwareExplorer on 2009-09-04
Is there an english page for that computer? I tried to switch the language, but it didn't take me back to the page that you linked to.

---

### Post by gr8108 on 2009-09-05
Sorry, I searched for the Gateway site at USA and there is no my model, so, the only specifications are in english. What do you want to know?
 
(To see specs just click wehre says "Especificaciones")

---

### Post by Fafler on 2009-09-05
Most Linux drivers are generic. Chances are that the one you have already works. Try

```
glxinfo | grep direct
```

in a terminal. If you get a line like

```
direct rendering: Yes
```

then the driver works. Are you experiencing any problems with the current driver?

---

### Post by gr8108 on 2009-09-05
I haven't installed Xubuntu yet, due to I'm checkin' if my hardware components will work under Xubuntu.

---

### Post by SoftwareExplorer on 2009-09-05
The intel drivers are usually included with ubuntu. You could boot into a liveCD and check.

---

### Post by gr8108 on 2009-09-06
Ok, about using glxinfo | grep direct, the answer is afirmative, but I discovered an easy to perform test> using chess and select 3D view. In this case my Intel X3000 driver has not support for OpenGL, so, it is not fully working.

Im running Xubuntu on LiveCD

---

### Post by SoftwareExplorer on 2009-09-06
I think you have to install another package for the default chess program in Ubuntu (And therefore probably Xubuntu) is able to do 3D, regardless of weather your card supports 3D.

---

