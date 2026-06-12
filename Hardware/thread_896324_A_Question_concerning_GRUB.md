---
title: "A Question concerning GRUB"
date: 2008-08-21
forum: Hardware
---

### Post by epolyach on 2008-08-21
Hi,
I've got Lenovo T61 with Win XPP preinstalled and I have installed an additional HDD along with a combo slim adapter and installed Ubuntu 7.10 there.
Now I want to switch the hard disks, since I use Ubuntu basically. I.e. I want to have the HDD with Ubuntu as the primary one, and DVD in the combo. And change DVD with win XPP when needed.
Please advise what to do with GRUB. Thanks in advance.

Evgeny.

---

### Post by silvanus2005 on 2008-08-21
You should enter in Bios and set the HDD with Ubuntu as Master and the other HDD as slave.

---

### Post by epolyach on 2008-08-21
This is not a good idea, I think. I want to install the Ubuntu HDD permanently, and use DVD in the combo. From time to time, I will use winXPP HDD in the combo. Since now GRUB is installed on winXPP HDD, my notebook wont boot linux without this HDD. What I need is:

1) Properly install GRUB on ubuntu HDD,
2) Remove GRUB from winXPP HDD and allow notebook to boot winXPP.

---

### Post by silvanus2005 on 2008-08-21
Then you should install the HDD on which you want to have Ubuntu on your laptop. After that, you can reinstall Ubuntu using a live CD, and GRUB will boot directly Ubuntu.
You may also use a tool, called Startup-Manager, to change  your options in GRUB very easy, using a graphical interface. You can install Startup-Manager using Synaptic Package Manager.

---

