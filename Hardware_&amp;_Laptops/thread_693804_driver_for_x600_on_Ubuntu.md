---
title: "driver for x600 on Ubuntu"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by marilari on 2008-02-11
hi all!!i have a laptop pc with ubuntu installed...i am a newbie and a try to install the driver of my ati radeon x600, going to driver whit restriction and enableing ati accelerated graphics driver...but i receive this error: Could not apply changes!Fix broken packages first.
Can anyone help me,please?

---

### Post by luisromangz on 2008-02-11
Your package list seems to be broken, and the restricted driver manager works using the package system to retrieve the driver, so it won't work until that is solved.

Try running this in a terminal:

sudo dpkg --configure -a

---

### Post by marilari on 2008-02-11
thank for your answer...i try to write it on the consolle but it write nothing

---

### Post by AlanR8 on 2008-02-11
At the risk of being flamed, try downloading Envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and installing the driver with the supplied script.......

---

### Post by marilari on 2008-02-11
> **AlanR8 said:**
> At the risk of being flamed, try downloading Envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and installing the driver with the supplied script.......

i try to install it but GDEbi says 
error: Dependency is not satisfiable: xserver-xorg-dev

what's wrong??

---

