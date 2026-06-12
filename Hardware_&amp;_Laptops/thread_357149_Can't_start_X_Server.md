---
title: "Can't start X Server"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by sanjeevdivekar on 2007-02-09
Hi,

I am newbie to linux. When I run Dapper Drake (received from ShipIt Project) I says "Can't find Config File, Can't start X Server". 

What is a problem?

Can I install UBuntu from console? sometimes i get console sometime doesnt.

I have PIII 1.2Ghz, Intel 810E Motherboard, 256MB RAM, 40GB HDD.


Thanks for Help,

Sanjeev Divekar

---

### Post by aberry5555 on 2007-02-09
Try typing in 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then

```
startx
```

This should hopefully create the configuration file then start the desktop, although by the sounds of it you might need special drivers if you have an onboard intel VGA card.

Post back if you get any problems

---

