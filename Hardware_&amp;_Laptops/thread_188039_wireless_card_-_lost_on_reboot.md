---
title: "wireless card - lost on reboot"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by neill on 2006-06-03
hi

very new to ubuntu, but learning fast !

managed to get my linksys PCMCIA wireless card working on an old vaio laptop using ndiswrapper, finishing up with

depmod -a
modprobe ndiswrapper

and the card is then configured in network settings and it works fine

but .............

i have to do 'modprobe' again when i reboot

how can i have this happen automatically ? :-k 

thanks

neill

---

### Post by neill on 2006-06-04
found it

ndiswrapper -m

---

