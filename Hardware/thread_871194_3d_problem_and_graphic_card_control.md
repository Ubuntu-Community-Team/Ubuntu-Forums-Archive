---
title: "3d problem and graphic card control"
date: 2008-07-26
forum: Hardware
---

### Post by david sousa on 2008-07-26
Hey!

I really don't understand nothing about hardware, drivers and their correspondent software. So I'm here to ask you for some help.

I would like to no if i can control my Intel Corporation Mobile GME965/GLE960 graphic card with Ati catalist control panel.

Because my screen starts flashing when i run things like stellarium and chess in 3d, and maybe this could be the solution.

In the other hand I'm able to use compiz cube, but not all the features like the water effect.

Well... Waiting for opinons...

---

### Post by Kubunteando on 2008-08-06
No, you cannot use ATI catalyist.
This is specific for ATI cards, and not even to all of them.

I have similar issues as you with my computer. I also have a GME965. The issues is that the Linux driver is not that good yet.

---

### Post by david sousa on 2008-08-07
So do I just have to wait for the updates???

---

### Post by Kubunteando on 2008-08-08
Since the drivers are very linked to the kernel I don't think any improvements will come before the next version of Ubuntu 8.10 in November...

---

### Post by s3a on 2008-08-08
Since it is an Intel card I think you will be having to wait for the next open source driver for your video card. So like Kubunteando said, you would proably have to wait for the next release of Ubuntu.

---

### Post by david sousa on 2008-08-08
Bah! Do i will have to reinstall everything in the next release or i just have to do the updates?

---

### Post by Kubunteando on 2008-08-08
Just update the version. That option will be available when the version 8.10 is out.

So you can install and configure your system with the current version and upgrade later on.

You don't need to reinstall or install from scratch.

---

### Post by david sousa on 2008-08-08
I would like to know if it does have anything to do with de 3d acelaration.

Because when i write in console:

> 
glxinfo | grep rendering

it doesn't respond absolutely nothing and it should say:

> direct rendering: Yes 

---

### Post by mikjp on 2008-08-08
If you are willing to take risks in your life you could try updating to Ubuntu 8.10alpha3 already now. Things might, however, be a bit rough... see [this page](http://www.ubuntu.com/testing/intrepid/alpha3).

Greetings,

mikko

---

### Post by david sousa on 2008-08-08
I could but i wont because im not such an experienced user to take that risk.

But i would like that someone could solve my last question please...

---

