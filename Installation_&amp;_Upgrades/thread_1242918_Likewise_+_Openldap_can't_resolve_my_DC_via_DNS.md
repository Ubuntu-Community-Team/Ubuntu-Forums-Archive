---
title: "Likewise + Openldap can't resolve my DC via DNS"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by ricster on 2009-08-17
I've got an OpenLDAP/Samba server running on a debian machine and have successfully (and very easily) joined two windows xp boxes to it but i'm having trouble getting ubuntu authed. I got likewise and likewise gui but in both instances i'm asked for the domain to join and then it errors stating it cant find the domain, instructing me to sort out my DNS. 

Can't i just join the domain and instruct it which IP the DC is sat at? Seems like a very obvious command line switch to add rather than being forced to use DNS, which the XP boxes didnt need me to do. 

When you run auth-client-config it asks for the IP address of an openldap server specifically, but that did nothing with the information i.e. letting domain users login to the box.

---

