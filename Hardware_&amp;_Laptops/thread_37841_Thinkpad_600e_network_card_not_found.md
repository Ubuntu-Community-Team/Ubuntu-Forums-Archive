---
title: "Thinkpad 600e network card not found"
date: 2005-05-28
forum: Hardware &amp; Laptops
---

### Post by greenenewb on 2005-05-28
we just removed win98se and loaded ubuntu 5.04 and after the installation we were unable to use the network card ( ibm etherjet pcmcia card ).  The device manager displays the 2 pcmcia slots but does not recognize the etherjet card.

Is this card supported?  and if so what configureation files do we need to update so it will recongize the card.

thanks

---

### Post by ::DoGG:: on 2005-05-29
Probably if the PCMCIA is working you just have to check which module is good for you network card (google )and load it. then go "dhclient eth0" end interface shold went up. Your card is for sure supported in linux, believe me, taht`s a must for pinguin system :D

---

### Post by IbeeX on 2005-06-16
Hello

I got same problem with IBM Ethejet Cardbus card it is not recognized by 'cardctl ident' but it is some problem with ubuntu PCMCIA module since this is PCI card ant it is recogniyed by lspci '0000:06:00.0 Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)'
and then all you need to do is make 'sudo ifconfig eht0 up'  and sudo dhcp client on eth0 and it is working

Ivan

---

