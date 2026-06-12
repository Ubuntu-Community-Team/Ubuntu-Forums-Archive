---
title: "2 ubuntus 1 crossover cable"
date: 2008-10-13
forum: General Help
---

### Post by liorc666 on 2008-10-13
&#65279;&#65279;&#65279;&#65279;hey i got my new PC (this machine) its has 2 network cards , one is connected to my router using DHCP and the other is connected to my old PC with a Crossover cable; i used Wireshark to see the logs and if the computer talking between them , i see the old computer(192.168.1.111) ARPing for (192.168.1.1 - whice is the router) and this machine (192.168.1.71) ARPing who have the old computer(*.111) , what am i doing wrong and how can i make them talk - i want to transfer data between them? (both of them running ubuntu 8.04 hardy)
note: im using ubuntu for 3 years now and i think im quite experienced with this.

---

### Post by fragos on 2008-10-13
Plug both PC's into the router and everything should work. You don't need to use IP addresses on your LAN. If both PC's have different host names they can be addressed as {hostname}.local and you won't need to be concerned over which IP DCHP has assigned.

---

