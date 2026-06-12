---
title: "Nvidia GT130m driver"
date: 2010-02-02
forum: Hardware
---

### Post by Linxu on 2010-02-02
Hello there (: 

I'm very new to linux and atm im using ubuntu 9.10 .. and i like it.. 

but. the problem is that im running with dual screen and the graphic driver
from nvidia wont allow me to use my second screen.. so i did go to nvidia to get the latest
(beta) driver.. but i just cant install it.. not with gedit or from the terminal, it writes something about i need to close xserver before i can install/unpack it.. 

any ideas or "step by step" guides to do this ? :) 

Specs : 
Nvidia GT130m
Ubuntu 9.10 64 bit

controlled by a newbish newb ^^

also.. is it possible to use webcam in Empathy `?

---

### Post by AimOn on 2010-02-03
From noob to noob.

Have a look at envyNG. This helped me to install the video driver.
But the driver somehow doesn't work for me...

If you have probs with the graphics after installing, then you might want to
```

sudo nvidia-xconfig

```Hope this helps...

---

