---
title: "Ubuntu internet problem"
date: 2008-07-12
forum: General Help
---

### Post by Vernal on 2008-07-12
Hey everyone, I am new to Ubuntu, and Linux in general; this is my first linux distribution I am trying. I begged my brother to install it on my pc, couldn't handle Vista anymore, but I am glad he kept vista on here so that I could ask for help:). He uses Granular, and he's not going to help me so I got to ask for help myself. 

Anyways, back to the reason I posted. After my brother installed Ubuntu, he set up the internet using the icon at the top right of my screen. I have a Belkin USB Adapter and it was able to find the network "linksys" easily. He typed in the password and it connected. I can connect to the internet and surf the web, but it is extremely slow, and for some reason, it randomly disconnects from the internet and I have to re-type in my password to re-connect to the internet. 

Strange thing is, when I run the online video game, Guild Wars Nightfall, it runs almost perfectly, little to no lag and the only problems I have is when the internet randomly disconnects.

So, what should I do? I searched the forums to see if anyone else had this problem but I couldn't find much at all.

Thanks for taking your time to view my post:biggrin:

---

### Post by werries on 2008-07-12
are you running guild wars in Vista or in ubuntu on wine?

---

### Post by Vernal on 2008-07-12
with WINE, and it runs perfectly! I used to run Guild Wars on Vista, but surprisingly, it runs terrible on there compared to gw with wine:)

---

### Post by werries on 2008-07-13
what sites are you viewing? some are going to be slower than others

---

### Post by ghost_ryder35 on 2008-07-13
try setting static DNS servers.  currently some drivers in linux get upset when the router itself is referenced as a DNS server (linksys does this unless the modem that it is connected to is set to bridged mode) and get very slow response.  so i would try right clicking on nm-applet and clicking edit connections.  then i would add static DNS servers such as public ones like
4..2.2.1
through
4.2.2.6
#Note if you edit "/etc/resolv.conf" it will get overwritten by network manager on reboot.

As for random disconnects..............................  IDK i have the same problem :)

---

### Post by Vernal on 2008-07-13
Thanks for all your responses guys. My brother changed the DNS servers that came with the isp to openDNS ones he got from opendns.com . So should I tell him to change them to static dns servers?

---

### Post by werries on 2008-07-15
i dont....know

---

