---
title: "IBM T30 WLAN Problem"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by rku on 2005-07-29
Hi there,

I just managed it to install ubuntu 5.04 on my ibm t30 laptop. The integrated wlan runs on windows xp without any problems.

First I used the gui, later iwconfig to config the wlan adapter. But the adapter was not willing to work in any way. dhclient said that the network was down... But how to start it anyway?

Hopefully,

Rku

---

### Post by phen on 2005-07-29
please give more information about your wlan adapter. which brand etc

the output of "lspci" is helpful, too  (type in a terminal!)

cheers,

kai

edit: 
another idea: search the wiki or google for installation help on t30. a lot of people installed linux/ubuntu on t30s before!

[http://tuxmobil.org/](http://tuxmobil.org/)

---

### Post by rku on 2005-07-30
Hi Kai,

thanks for you quick answer:

lspci says:
Prism 2.5 Wavelan Chipset, by Intersil Corporation 

I will have a look at the wiki to see if they can help me. I ll post the results.

regards

Rku

---

### Post by rku on 2005-07-30
[QUOTE=rku]Hi Kai,

thanks for you quick answer:

lspci says:
Prism 2.5 Wavelan Chipset, by Intersil Corporation 

I will have a look at the wiki to see if they can help me. I ll post the results.

regards

Rku[/QUOTE]
 Well. Wiki does not say anything, but I got I working finally:

first I configured the adapter with iwconfig, told everthing to be "auto". The important thing what is never mentioned: restart your network using "/etc/init.d/networking restart". Then I could see that the ap was found. Finally I added the wep key using iwconfig <interface> key <wepkey>. Restarted network once more and : there you are. It works.

Thanks a lot,

Rku

---

