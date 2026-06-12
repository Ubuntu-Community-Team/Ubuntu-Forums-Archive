---
title: "Older Laptop graphic problem"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by pricyber on 2008-01-16
I am trying to install Ubuntu 7.10 on a older laptop(Acer C100) after loading the live CD the colour is all distorted(probably running in 16 colour mode), Then I run it in graphical safe mode, than the screen just went black... I let it sit for a night, and nothing happens.

Is there way to install driver or something so i can see some colours?

---

### Post by Yellow Pasque on 2008-01-16
What kind of graphics chip does it have?

---

### Post by polmir on 2008-01-16
please post the output of the following command:

```
lspci -m
```

---

### Post by jerrykenny on 2008-01-16
I couldnt say for sure but

after loading the live CD the colour is all distorted(probably running in 16 colour mode), 

sounds like an overloaded monitor. If so, this will damage the monitor. When you go for your next install attempt, use the older traditional graphics

Look at the boot-options b4 you press enter to see how you do that.

---

### Post by pricyber on 2008-01-17
[http://global.acer.com/products/notebook/tmc100/spec.asp](http://global.acer.com/products/notebook/tmc100/spec.asp)

Thats the spec, it can run Windows XP in 16-bit colour, so I think is just a driver problem 

As in 16 colour I couldnt run lspci -m, but is there way to run the system without Gnome so I can set things up/

I tried using different distro, ie Kubuntu, Ubuntu, Xubuntu, all have the same problem, thats when I finish installing using the alternate CD

i have manual change to use the  manual changing the bit colouring to 8-bit in recovery mode using dpkg-reconfigure xserver-xorg which  show a different type of mess up

---

### Post by pricyber on 2008-01-17
Problem solved, by playing around with xserver-xorg configure

---

### Post by psilokan on 2008-02-17
Care to elaborate on how you fixed it?  I have a C100 and am having the exact same issue.

---

### Post by jc8458 on 2008-02-19
I have been trying to get this working on my C100 for ages and despite much messing with my x configuration I  kept having to resort to Ubuntu 6.06. Could you please post your config file.
Many thanks.

---

