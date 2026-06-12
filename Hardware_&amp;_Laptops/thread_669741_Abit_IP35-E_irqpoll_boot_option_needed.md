---
title: "Abit IP35-E irqpoll boot option needed"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by Cuppa-Chino on 2008-01-16
Hi I have an Abit IP35-E motherboard

it has Intel ICH9 southbridge and the jmicron ide controller.
* intel e6400
* nvidia 7900
* 1 samsung 1204 120gb sata hd
* 1 samsung 2503 250gb sata 2 had
* 1 lite-on dvd-writer IDE
* 1 pioneer dvd-rom IDE

the boot sequence always fails at looking for root drives and there seems to be an interrupt issue - I am not sure though, when I include the irqpoll parameter in the boot line it boots fine.

higher spec boards from abit and others have the option to set sata to achi, this board does NOT have an option to set the Sata channels to AHCI in the bios!

I would be grateful for any help that could be given in getting the board to work properly -- I am currently using gutsy amd64

---

