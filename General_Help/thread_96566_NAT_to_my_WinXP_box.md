---
title: "NAT to my WinXP box"
date: 2005-11-29
forum: General Help
---

### Post by eonix on 2005-11-29
Hello!

I was wondering if it is possible to set up my Ubuntu box to forward a port to my WinXP box. The setup I have at home is as following: 

DSL Router Modem running DHCP with 4 ethernet ports, port 22 forwarded on the DSL router to my Ubuntu box. I want to run tightVNC on my XP box but want to use a SSH tunnel to do this so that the data transfer is encrypted and not visible to the outsideworld since the port for tightvnc wont be opened on the DSL router.  

Is it possible then make a ssh tunnel to my ubuntu box and have it forwarded to my XP computer? 


Eonix

---

### Post by greenway on 2005-11-29
I don't really get your configuration... Are your XP box and Ubuntu box on the same network? IP masquarading is only possible on a router so then Ubuntu should be routing between a network with you XP box and another network. If you could be a little more clear we should be able to come up with a solution...

---

### Post by eonix on 2005-11-29
Hey. 

XP and Ubuntu are on the same network. They both get their IP's from the DSL Router, 10.0.0.1 = Ubuntu and 10.0.0.2 = XP

---

### Post by greenway on 2005-11-29
When both on the same network, your connecting between the your Ubuntu box and the XP box don't go through the router. When connecting from your XP box, you will first go through your local network; your router (which will most probably also be configured to be your gateway) will only be passed when the IP you're looking for is not found on your local network (take a look at your route table). Also, on your local network, there is no need for a secure shell connection (supposed you have your router performing some sort of firewall function).

If all you want to do is run some sort of remote administrative tasks from between two computers on your local network, just set the Ubuntu machine up as the server and your XP box as the client (assuming you will be performing administrative tasks from your XP box to your Ubuntu box) and you're good to go!

[EDIT] to much Singa beer, please don't mind the typo's. Thanks![/EDIT]

---

