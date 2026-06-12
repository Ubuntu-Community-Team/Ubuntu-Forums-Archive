---
title: "X server issue - fatal error"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by ~Speed on 2006-01-31
Hello :)

I am newish to Linux in general and new to Ubuntu in particular.

I have AMD64bit computer, after install is completed X server wont start.

**Here is what it says:**

*fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.*



OK, I have read some suggestions here on how to fix this, I restarted X server config, changed some settings, to no avail.

I think my graphic cart is not supported:
ATI radeon, sapphire PCI-ex-16, x800 GTO2, 256MB.

How do I fix this, please?

And, I have two left hands when it comes to command line...
:( 

Please, help.

spd

---

### Post by ~Speed on 2006-02-01
Anyone?!

---

### Post by dcstar on 2006-02-01
[QUOTE=~Speed]Hello :)

I am newish to Linux in general and new to Ubuntu in particular.

I have AMD64bit computer, after install is completed X server wont start.
.......
Please, help.

spd[/QUOTE]
sudo dpkg-reconfigure xserver-xorg

and select the VESA video driver, that should get you a basic X system working and then you can look at getting the right driver for your hardware.

---

### Post by ~Speed on 2006-02-01
[QUOTE=dcstar]sudo dpkg-reconfigure xserver-xorg

and select the VESA video driver, that should get you a basic X system working and then you can look at getting the right driver for your hardware.[/QUOTE]

Thank you dcstar! :) 

How do I get the right driver, pls?

---

