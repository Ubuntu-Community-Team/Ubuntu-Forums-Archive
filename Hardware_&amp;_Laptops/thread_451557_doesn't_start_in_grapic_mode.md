---
title: "doesn't start in grapic mode"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by ipatec on 2007-05-22
Hello,
I have a laptop (Dell Inspiron 6400, Core 2 Duo, 1 GB RAM, 120 GB HDD, Ati X1400 video)
I've just installed Ubuntu Studio 7.04, and it doesn't start in graphic mode, and I also receive an error, something like server x can't determine graphic....or something like this
Can someone help me please?What do I have to do?Can I repair it from console, if yes, can someone make me a guide please?

I must tell you that I was having the same problem on CentOS 5 and Ubuntu 7.04
CentOS 3 works, and Mandriva. But I want Ubuntu Studio :)

---

### Post by ipatec on 2007-05-22
The errors are:
Failed to start the X server (your graphical interface) It is likely that is not set up correctly...and ask me if I want to see the X server output to diagnose the problem.I select Yes and:
the is something like fatal server error: Caught signal 11. Server aborting
I push Ok, and I see something like bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed

Any advice please?

---

### Post by Abhijit_T on 2007-05-22
try this when ur in text mode -
```
sudo apt-get install xorg-driver-fglrx
```

After its downloaded and installed, type-
```
startx
```

That should do it

If it says package not found, make sure u've got the proper repositories enabled(universe, etc.). Search elsewhere in the forum for tips on enabling them.

---

### Post by ipatec on 2007-05-22
It says that it can't find the package xorg-driver-fglrx
Any adive please?thank you!

---

### Post by klangfang on 2007-05-22
A wonderful to all ...

i installed the ubuntu freshly and have the same problem.

i tried to install the xorg-driver package, but he couldn't find it. I think the laptop can't connect to the internet, but i don't know how to set up my ethernet device. How do i do that....

Thx for help

---

### Post by ipatec on 2007-05-22
I solved the problem with this tutorial:
[http://ubuntuforums.org/showthread.php?t=399913&highlight=dell+6400](http://ubuntuforums.org/showthread.php?t=399913&highlight=dell+6400)

---

