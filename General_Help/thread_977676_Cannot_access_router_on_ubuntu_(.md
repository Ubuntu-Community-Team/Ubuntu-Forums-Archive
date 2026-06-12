---
title: "Cannot access router on ubuntu :("
date: 2008-11-10
forum: General Help
---

### Post by milky87 on 2008-11-10
Hi everyone, I'm new for ubuntu. I am using ubuntu8.04. My problem is I can't access my router at all. At first, I could access very well, but now nothing happens when I am trying to access the router. I am using winxp too. In winxp, I can access very clearly.I tried to change eth1 by using dhcp automatically or static IP Lan address. (eth0 on my computer is not disabled) But It still doesn't work. 
Anybody helps me plz? Thanks a lot!

---

### Post by oilchangeguy on 2008-11-10
> **milky87 said:**
> Hi everyone, I'm new for ubuntu. I am using ubuntu8.04. My problem is I can't access my router at all. At first, I could access very well, but now nothing happens when I am trying to access the router. I am using winxp too. In winxp, I can access very clearly.I tried to change eth1 by using dhcp automatically or static IP Lan address. (eth0 on my computer is not disabled) But It still doesn't work. 
Anybody helps me plz? Thanks a lot!

are you using a wired or wireless connection? wireless is wlan0.

---

### Post by phillik747 on 2008-11-10
What kind of router? Can you ping the ip address of the router when in Ubuntu?  Also try cleaning your Mozilla cache and trying again.  Routers are funny that way.  I run dd-wrt and have noticed that it doesn't like Mozilla for whatever reason so when working on my router I fire up IE. *(I can access it with Mozilla but when making changes it doesn't seem to erase the old ones at times...YMMV)*

---

### Post by Adriweb on 2008-11-10
what do you mean by "access" your router?

is it that you are trying to configure the router? what are you trying to do? How do you do it in XP?

---

### Post by milky87 on 2008-11-11
> **Adriweb said:**
> what do you mean by "access" your router?

is it that you are trying to configure the router? what are you trying to do? How do you do it in XP?

I mean "access" is that I can ping my router. I am using a wired ethernet (not onboard). My router is Zynxel. I think the problem is ubuntu. I can not ping my router. So I guess that ubuntu can not detect my network card.

When I in XP, I can access the internet well.In UBUNTU sometimes I can do that but now I can't. Any suggestion plz?

---

### Post by Neo_The_User on 2008-11-11
Can you access the internet or just your router? Be sure that your router's gateway address is correct because if you type in the wrong number, it will time out.

---

### Post by phillik747 on 2008-11-11
> **milky87 said:**
> So I guess that ubuntu can not detect my network card.

Please give a print out of ifconfig

---

