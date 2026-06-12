---
title: "Dell 1545 Yukon 88E8040 ethernet not working with 9.10"
date: 2009-12-02
forum: Hardware
---

### Post by romain_quidet on 2009-12-02
Hi all,

I've been using Debian for more than 10 years, Ubuntu now for 2 years, nice flavor! I installed the 9.10 on my new 1545, but the ethernet card refuse to work... 

Sky2 module reports correctly the card, but always complain that the link is not ready (working under windows also present on my laptop)... I tried to change speed with mii-tool, nothing can work...

I installed sk98lin driver also, crashing ... 

Anybody knows how  to make this card working with sky2 module ? I read something about the acpi=off, I tried it but it's not working for me... 

Thanks! 
Romain

---

### Post by romain_quidet on 2009-12-04
I reply to myself, it can help people !

sky2 module works fine with ubuntu 9.10 and Yukon 88E8040 ethernet controller, but the autonegociation and speed setting does not work correctly.

I used 
sudo mii-tool -A 10BaseT-FD 

to relaunch the autonegociation with my linksys router. It worked. 

I tried before a mii-tool -F 10BaseT-FD which is not working ... One week to find that !

Romain

---

