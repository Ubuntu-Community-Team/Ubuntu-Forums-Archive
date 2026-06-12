---
title: "ls /dev/ finds no ttyUSB*"
date: 2013-08-03
forum: Hardware
---

### Post by Bucephalus01 on 2013-08-03
Hi

I'm trying to do some development with an am335x starter kit. And part of the process is to obtain access to the usb ports on my linux box.
I have two environments. Ubunut 12.04 on VMWare on a windows 7 computer and Ubuntu 13.* (i.e. the latest) installed as the sole occupant on antoher computer.
When I go  ls /dev/, there is no ttyUSB in either of these installations. Yet, when I put a USB into the port of the linux 13.0* box I can access it.
Does anyone know why the ttyUSB* isn't showing in the /dev/ directory? Is it somewhere else?
Or if not, how do I get these USB ports into this directory?
David.

---

### Post by Bucephalus01 on 2013-08-03
Hi

Thanks. I worked it out. I didn't realise that the ttyUSB was on my starter kit. I thought it was something inside the computer. All I had to do was plug it into the computer and turn it on and ttyUSB0 and ttyUSB1 appeared in the dev directory.

David.

---

