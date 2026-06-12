---
title: "adsl connection probs... pls help :("
date: 2005-11-13
forum: General Help
---

### Post by trandojedi on 2005-11-13
hi... after finding out how cool ubuntu 5.10 is with my ibm t23 laptop and in general i decided to replace SUSE 9.30 with it on my desktop...

i have problems with networkiung though... my motherboard (Intel D865PERL) has an inbuilt network card. i have adsl. on my laptop i got adsl working by clicking on the icon in the top right of the screen for networking, changing eth0 to DHCP and then running pppoeconf... this worked.  The problem with my desktop is that that icon is not there, i'm thinking ubuntu is having problems with detecting the network card. if i go to admin -> networking it shows that the eth0 is there, i enable it but it still doesn't show up in the right top corner and if i run pppoeconf it still doesn't work... like i said i think it's to do with the motherboard, because in windows i had to install some drivers to get it working... if anyone has this motherboard or knows wat to do to get adsl going pls help :)... otherwise i might just have to go out and buy a network card :( eeep 

cheers garrick

---

### Post by zman58 on 2005-11-13
I recently set up UBUNTU 5.10 on a ADSL ISP. I had to use a fixed or static ip address. I first tried DHCP, but could not get it to connect. Apparently the ISP was not providing the network settings to the UBUNTU system. I used a typical internal address (192.168.1.8) with netmask 255.255.255.0. After that, things started working.

Now I have a question for you. Since you have two systems, why don't you get a WAN router?

If you have more than one system that you want to use (Notebook and laptop), then you should make things simple and pick up a WAN router. You just setup the router to access your ADSL service provider. Most WAN routers have 4 RJ45 jacks on them (wireless ones have this too). They can connect to ISP using PPPOE. They provide DHCP services to the subnet. All you have to do is set up your systems with DHCP. No PPPOE config required! Just plug your workstations into the WAN router and go! They even provide you with a decent firewall on the ISP side. You can pick up a WAN router for around $20-$40. Something like the Motorola model WR850G or the LinkSys model (whatever it is). They are easy to set up and connect to your ADSL service provider.

---

### Post by zman58 on 2005-11-13
The smiley got in the way because I used a paren. The network address was 102.168.1.8. on that last post. Sorry.

---

### Post by trandojedi on 2005-11-14
hmmm cheers for that... i'll check out some WAN routers since i got quite a few computers connected to the same adsl through a hub (i.e like 5 computers connect to thje same adsl)... hmmm just a couple questions though... my adsl requires a username and password. would a router accomodate that?

---

