---
title: "Toshiba A110 Atheros Integrated Wireless Card Not Working"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by Galactic Jack on 2007-07-03
I've installed Ubuntu Dapper 6.06 on my laptop a couple of days ago because for the past 6 months I've been using it on my Desktop Computer. Everything on the laptop seems to work great, my touch pad's fine, my screen's a good resolution, keyboard works, just about everything EXECPT MY WIRELESS CARD!

This has prooved to be a HUGE pain in the assbecause I've been trying to install everything from ndiswrapper to madwifi, the net5211.inf file... just about everything I could find on the subject... and NOTHING has worked from ANY of them. the only even relative success I've had with this is when I install ndiswrapper and type ndiswrapper -l and find that NetopOEM.inf has found both the hardware and driver. BUT, the big thing is getting it to recognize the card in System > Administration > Networking.

I've been working on this for about 3 days straight and I'm very tempted to give my laptop a smiley since nothing will work.

GJ

---

### Post by ugm6hr on 2007-07-03
Post the output from:
```
lspci
ifconfig
iwconfig
```
You are looking for Ethernet/Network Controller info.

---

### Post by Galactic Jack on 2007-07-03
Bah I just switched to Feisty and it works fine. 

Crisis averted

GJ

---

