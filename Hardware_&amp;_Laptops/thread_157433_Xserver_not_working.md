---
title: "Xserver not working"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by howzat117 on 2006-04-09
Hi there. i hope this is the right forum to post in. first go at linux. i have been tryin to get Breezy badger up on an old(ish) system of mine.

pentium 3, 667Mhz
192 RAM
10 GB disk
has an intel intergrated graphics, but i also have a Voodoo 3fx on PCI which i am using as main.

i first tried to install typical system, but when it tried to start, it just hang with a black screen and white underscore in the top left hand of the screen, not blinking. so i tried to low memory/server/lightweight install. base xserver core etc. installs ok. but then when i type startx at command it returns with error saying screens found, but none have a usuable configuration. 

is there an easy way to export the log file from the linux box so i can post it here?

many thanks,:-D 

Si

---

### Post by howzat117 on 2006-04-09
nevermind. fixed it myself. went through the logs and it seems that the deafult was picking the wrong pci bus, so changed xorg.conf to pick up voodoo 3 pci bus. its all good! ubuntu here i come! :D

---

### Post by Mustard on 2006-04-09
[QUOTE=howzat117]nevermind. fixed it myself. went through the logs and it seems that the deafult was picking the wrong pci bus, so changed xorg.conf to pick up voodoo 3 pci bus. its all good! ubuntu here i come! :D[/QUOTE]

You've excelled. :)  Well done!

---

### Post by howzat117 on 2006-04-09
thanks 8-) guess its a bit of a long shot, but i am going to try the main install again. last time, the system kept hanging when starting up xserver. now i know the problem, is there a way to bypass the xserver auto load and boot into bash so i can manually edit the conf file?

thanks again :) 

Si

---

