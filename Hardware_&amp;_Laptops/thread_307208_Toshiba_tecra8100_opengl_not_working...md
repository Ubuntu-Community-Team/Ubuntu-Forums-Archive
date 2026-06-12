---
title: "Toshiba tecra8100 opengl not working.."
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by Tristam on 2006-11-26
Hello! I just installed Kubuntu 6.10 on an old laptop (toshiba tecra 8100) which has a savage graphics card (dont know more details). Anyway, it work fine but anything using opengl just freezes. glxinfo says Direct Rendering is working and glxgears wont run and says: libGL warning: 3D driver claims to not support visual 0x42.

Does this mean the old savage card just doesnt know opengl or could something be done about it..

thanks for any help

---

### Post by Tristam on 2006-12-02
mmm.. hello? doesnt anyone know anything about that error message saying **"libGL warning: 3D driver claims to not support visual 0x42"** ???? is it possible to use opengl or not? please help :)

---

### Post by dmizer on 2006-12-02
actually i have the same machine ... two of 'em.  you should pay attention to your cpu fans.  i burnt up some memory slots and a pcmcia card before i learned how to turn the fan on manually.

the tecra 8100 has an s3 virge card (often misidentified by linux as savage) ... which was one of the first (if not THE first) video card to support 3d rendering. but performance is the worst.  i wouldn't suggest pushing your machine into the 3d envelope.

although your machine can technically handle it, the case design doesn't allow for enough ventilation to keep your cpu cool.  also, because of that ... i'd suggest something a bit lighter like xubuntu because even with your full compliment of 512 meg of ram, i think kubuntu's pushing things a bit.

definitely do keep an eye on your cpu temps no matter what you do though.

edit: i'll be, i just did some hunting and discovered we do indeed have the savage rather than the virge card.  the savage is still based on the virge, but is significantly better at 3d rendering.  i still say the machine is not physically capable of handling it even though it's technically able to handle it.

---

