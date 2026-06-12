---
title: "Lenovo B560 Nvidia driver"
date: 2012-03-19
forum: Hardware
---

### Post by Syncope on 2012-03-19
Hello, I have a Lenovo B560 laptop with Nvidia Geforce 310m graphic card and am using Xubuntu 11.10.
I just managed to instal drivers from Nvidia website (290.10), but when I restart, Xubuntu splash appears but then it goes black console with some lines like stop blabla (ok), start blabla (ok) and then it does nothing. The only think I can do get graphic enviroment back is 
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
startx
```
but then, if I understand it right the graphic is running on integrated Intel graphic device, not the Nvidia card.

Can someone help me out? I couldn't get any advice on our Czech forum.

---

### Post by mraandtux on 2012-03-19
Try Bumblebee?
Project Website:[http://bumblebee-project.org/](http://bumblebee-project.org/)
Installing Instructions: [https://github.com/Bumblebee-Project/Bumblebee/wiki/Install-and-usage](https://github.com/Bumblebee-Project/Bumblebee/wiki/Install-and-usage)

---

### Post by uRock on 2012-03-19
Hello and welcome to the forums.

When you open the Additional Drivers application does it offer any drivers?

---

### Post by Yellow Pasque on 2012-03-19
> **uRock said:**
> Hello and welcome to the forums.

When you open the Additional Drivers application does it offer any drivers?
jockey will offer Additional Drivers because it's fairly naive about Optimus or other hybrid graphics system. Installing the drivers jockey offers on such a system = no joy (and probably a trip to recovery console). Please be careful with such advice.

---

### Post by uRock on 2012-03-20
> **Temüjin said:**
> jockey will offer Additional Drivers because it's fairly naive about Optimus or other hybrid graphics system. Installing the drivers jockey offers on such a system = no joy (and probably a trip to recovery console). Please be careful with such advice.

Every time I have installed the offered driver in Additional Driver I have been happy. I have never been given a reason to doubt the usefulness of Additional Drivers. Do you have any constructive input?

---

### Post by Yellow Pasque on 2012-03-20
> **uRock said:**
> Every time I have installed the offered driver in Additional Driver I have been happy. I have never been given a reason to doubt the usefulness of Additional Drivers. Do you have any constructive input?
Have you ever used jockey on a hybrid GPU system? Is this bug report constructive enough for you? [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/660443](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/660443)

---

### Post by uRock on 2012-03-20
> **Temüjin said:**
> Have you ever used jockey on a hybrid GPU system? Is this bug report constructive enough for you? [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/660443](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/660443)

By constructive, I mean help the OP. The OP appears to already know how to remove a bad xorg.conf, so installing a driver via Additional Drivers would be worth the effort.

---

### Post by Yellow Pasque on 2012-03-20
The advice in post#2 (i.e. using bumblebee) is the route to go for Optimus systems.

---

### Post by Syncope on 2012-03-22
The additional drivers don't offer me any, just a wifi broadcom driver which is even not working on my laptop. I tried the bumblebee project but I couldn't figure it out. Actually, my graphic enviroment got somehow messed up so I'm up to reinstall Xubuntu, I think.
For the optimus thing, when I change graphic device in BIOS from IGD (or IDG?) to Optimus, so lspci could even find my graphic card, my laptop is overheating and fan almost won't stop. I don't know, maybe I just give it up, I wanted to install the graphic driver for Nvidia in faith the Blender will render faster etc., but I need a functional pc for school every moment and these attempts are just making me crazy.

---

