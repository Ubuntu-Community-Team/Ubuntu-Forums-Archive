---
title: "Feisty 7.04 (i386) and nvidia GeForce 440go (Dell Inspiron 8200)?"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by chene on 2007-08-17
hi all,

I'm installing Ubuntu 7.04 on a Dell Insprion 8200 laptop.  It has a pantium-4 and GeForce 440-go video card.  Everything works at this time (even my SMC wireless PCMCIA card) including the video card (using nv driver).

However, I would like to get 3D acceleration working by using nvidia driver.  I have tried 2 methods to install the nvidia driver:

1) using automatix, and
2) enable nvidia driver using restricted driver manager.

In both cases, the screen simple turned to black (actually off, I believe) as soon as gdm started.  I have also tried using a working xorg.conf and simply replaced "nv" with "nvidia" in the Driver section but the screen still turned black upon x-restarting.

I don't have my laptop with me at the moment so I cannot post the xorg.con now.  But can someone please confirm if the driver works at all before I further twick the xorg.conf by hand?

any help is very much appreciated,

---

### Post by phenest on 2007-08-17
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg

```
When you see the list of drivers, choose nvidia. Skip through the rest. When you're back at the prompt press Ctrl-Alt-Backspace, then:
```
sudo /etc/init.d/gdm start
```
If it says "Fail", type it again until it says Ok.
Wait for a moment and you should get a graphical login screen.

Voila!

---

### Post by chene on 2007-08-17
thanks for the VERY quick reply!  I'll try it tonight when I get home and report back.

---

### Post by chene on 2007-08-19
Thanks for this wonderful forum.  I have fixed my blank-screen problem by adding the following line to xorg.conf (under "Screen"):

 Option "UseDisplayDevice" "DFP-0"

---

### Post by duffrecords on 2007-08-21
I also have an Inspiron 8200 laptop and used to get the black screen after enabling the NVIDIA restricted driver.  Once I added the UseDisplayDevice option, it worked.  Thanks!

---

