---
title: "Internet: What do I do?"
date: 2008-08-14
forum: General Help
---

### Post by Kong on 2008-08-14
Just got Ubuntu (installed with Wubi) a few minutes ago, I'm excited. Decided I'm come online for a second and... nothing. I assumed Ubuntu would automatically find my router. I just need to know what I need to do to set up my internet connection.

Apologies for being so new to this stuff. :(

---

### Post by jualin on 2008-08-14
Welcome, first we need to know if you are using a Wireless card or an Ethernet card. And then we will need you go to the terminal and type > lspci
lsusb and then post the results on the forums to help you install the drivers on your computer.

---

### Post by Mgiacchetti on 2008-08-14
It would, but that would defeat the purpose of learning. (trying to be funny, guess it didnt work)

Anyway, you need to set up, 
your IP address,  (if your static or dynamic, it don't matter, unless you have a custom f/w on the router, like say, dd-wrt latest and greatest?  then dynamic will be a problem. If you have other computers i would use something like 192.168.1.200)

Subnet Mask, (255.255.255.0)
Default Gateway (should be the address to the router, 192.168.1.1 but might be different, refer to your router documentation)

DNS Servers (these are important, without dns servers, you cannot lookup names i.e. [www.google.com](www.google.com) vs  216.239.51.104)

---

### Post by jualin on 2008-08-14
Also go to the terminal and write > iwconfig 
ifconfig and post the results on the forums. Good luck!

---

