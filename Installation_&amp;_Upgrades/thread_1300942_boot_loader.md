---
title: "boot loader"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by alin19 on 2009-10-25
hello

i'm reading from a book how to make my own kernel;

and it says here abouth the boot loader lilo;

on my laptop  i run just 1 so ( ubuntu 9.04)

and i don't find the lilo conf file, ubuntu runs a different boot loader?

---

### Post by raymondh on 2009-10-25
> **alin19 said:**
> hello

i'm reading from a book how to make my own kernel;

and it says here abouth the boot loader lilo;

on my laptop  i run just 1 so ( ubuntu 9.04)

and i don't find the lilo conf file, ubuntu runs a different boot loader?

Ubuntu uses GRUB.

---

### Post by ibutho on 2009-10-25
Most distributions no longer use LILO. GRUB has been the default for several years now.

---

### Post by alin19 on 2009-10-25
> **raymondhenson said:**
> Ubuntu uses GRUB.

thanks, and where is the conf file located if you can tell me please; 

thanks

---

### Post by raymondh on 2009-10-25
to edit my GRUB, I have always used (from terminal)

```
gksudo gedit /boot/grub/menu.lst
```

is that what you were looking for?  If so, Herman's got a great GRUB page for reference:

[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

Remember to back-up.

---

### Post by yermandu on 2009-10-25
Grub 0.97 

Have too much support in many foruns, blogs, ircs. 
You can have many control with grub 0.97, like boot linux, windows, opensolaris, beos, too much operation system.

You have to install, and edit /boot/grub/menu.lst

---

### Post by alin19 on 2009-10-25
> **raymondhenson said:**
> to edit my GRUB, I have always used (from terminal)

```
gksudo gedit /boot/grub/menu.lst
```is that what you were looking for?  If so, Herman's got a great GRUB page for reference:

[http://members.iinet.net.au/~herman546/p15.html]("http://members.iinet.net.au/%7Eherman546/p15.html")

Remember to back-up.
thanks guys

---

### Post by raymondh on 2009-10-25
> **alin19 said:**
> thanks guys

you're welcome.

Happy ubuntu-ing.

---

