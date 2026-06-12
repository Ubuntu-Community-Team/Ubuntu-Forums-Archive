---
title: "dpkg to install LAMP"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by Martyn12 on 2008-12-20
Hello pros. 

I am an Ubuntu tinkerer and in the past have installed the Server edition. One thing I remember towards the end of the install process was dpkg ran with a certain number of packages listed in a terminal to mark (with a *) to install. 
Examples were DNS, LAMP, Kubuntu desktop etc etc. 
I am currently running Ubuntu desktop 8.10 on a laptop machine and would like to run the dpkg package to install LAMP. I know there are other workarounds to do this (such as apt-get and aptitude) but I particularly like the way dpkg seemed to deal with it. 

So, my question is, does anyone know how to invoke this installation program? I have done it before and cannot remember how!

Thanks in advance,


Martyn.

---

### Post by Rocket2DMn on 2008-12-20
Here you go:
```
sudo tasksel
```
will get you to that type of screen.  You can also flat out do
```
sudo tasksel install lamp-server
```

---

### Post by Martyn12 on 2008-12-21
Thanks. Actually - this is what runs on the server install and not the dpkg that I mentioned. 

Much appreciated. 

Martyn.

---

