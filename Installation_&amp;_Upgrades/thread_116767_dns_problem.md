---
title: "dns problem"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by murkus on 2006-01-13
I've recently installed ubuntu on my dad's computer. There's one major annoyance that's bugging me. 

I can't connect to servers with apt-get (or gaim or xchat). I've located the problem to the dns resolution. All connects are pointed to 1.0.0.0 instead of the real IP. 

I can reach websites with firefox though..

The comp is connected to the internet through a asdl modem/router, which I'm not very familiar with.

Could you point me to the right direction to solve this problem?

many thanks,

murkus

---

### Post by Thirsteh on 2006-01-13
Sounds to me like one of those bandwidth limiters/routers. You're sure you're not behind some paranoia-firewall that dumps everything else than ports 80 and 8080? (Standard web server ports)

---

### Post by Mr_Grieves on 2006-01-13
[QUOTE=murkus]I've recently installed ubuntu on my dad's computer. There's one major annoyance that's bugging me. 

I can't connect to servers with apt-get (or gaim or xchat). I've located the problem to the dns resolution. All connects are pointed to 1.0.0.0 instead of the real IP. 

I can reach websites with firefox though..

The comp is connected to the internet through a asdl modem/router, which I'm not very familiar with.

Could you point me to the right direction to solve this problem?

many thanks,

murkus[/QUOTE]
If you can reach website with firefox it's NOT a DNS problem. Hehe. If you can reach [http://ubuntuforums.org](http://ubuntuforums.org) or any other domain name, then DNS is working just fiiine. You have some kind other problem.

Try connecting you're computer directly to you're modem, not via a router and see what happens. OR, try and read the manual of the router you're using so that you're not blocking off traffic or need to turn on some port forwarding for example IRC..

---

### Post by murkus on 2006-01-13
[QUOTE=Thirsteh]Sounds to me like one of those bandwidth limiters/routers. You're sure you're not behind some paranoia-firewall that dumps everything else than ports 80 and 8080? (Standard web server ports)[/QUOTE]

The router (A-Link RoadRunner 24AP) has built-in firewall and NAT. I'm starting to think it's the culprit. Unfortunately I've no idea how to configure it properly.. :(

murkus

---

