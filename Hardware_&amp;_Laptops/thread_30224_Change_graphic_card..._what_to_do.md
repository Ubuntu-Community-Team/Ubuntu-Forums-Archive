---
title: "Change graphic card... what to do"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by Sonic-NKT on 2005-04-27
Hi,
since i cant get my 9200 to work with 3D and fglrx i thought about change the graphic card with another one i have in another pc (a Geforce 4200)
now i want to know what things i should do before i change and maybe after..
i dont want to mess up my nice system ;)

---

### Post by RuKK on 2005-04-27
Remove ATI specific drivers, and change the driver in your xorg.conf from whatever it is to "nv". That should work fine for getting up and running, then you'll want to install the binary nvidia drivers (which will involve chaning "nv" to "nvidia").

---

