---
title: "Cofiguration File For aticonfig --initial"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by Mithrandir06 on 2007-09-24
Ok, I am extremely new to Linux and am having much trouble with my ATI xpress 200m integrated graphics card on my HP pavilion laptop.  I use envy to install the latest ati drivers and now am wanting to configure the configuration file so i can get the graphics to work.  I don't even know if what I jsut said made sense...  but here is my problem from the terminal.

mithrandir@mithrandirs-laptop:~$ sudo aticonfig --initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
mithrandir@mithrandirs-laptop:~$ 


so how do i get a configuration file or what do i do from here to get the graphics to work?

please help :-/

P.s.  I also have a AMD Turion 64 and ive heard that 64-bit might pose problems too.

---

### Post by pointone on 2007-09-25
```
dpkg-reconfigure xserver-xorg
```

---

