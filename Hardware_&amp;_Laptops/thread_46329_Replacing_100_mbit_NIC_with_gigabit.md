---
title: "Replacing 100 mbit NIC with gigabit"
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by [CTG]ChAoS Overlord on 2005-07-04
I am thinking of replacing my 100 mbit NIC in my ubuntu file server by a gigabit NIC (realtek chipset) but I am afraid this will give me installation problems.

Can I just replace the NIC without worries, or do I have to take some precautions in mind? This fileserver is a critical machine in my network and can't be down for hours on end.

---

### Post by WildTangent on 2005-07-04
do you have a router with a gigabit switch? of not, then the gigabit NIC will only perform as fast as your routers switch, which is most likely only 100 mbit/sec

-Wild

---

### Post by Nolgthorn on 2005-07-04
I use a Gigabit NIC with my home machine, it works fine in Hoary.

---

### Post by WildTangent on 2005-07-04
[QUOTE=Nolgthorn]I use a Gigabit NIC with my home machine, it works fine in Hoary.[/QUOTE]
i would have to hope so if your paying ~$50 for it, but if the rest of your networking equipment is 100 mbit, than the upgrade is useless

-Wild

---

### Post by [CTG]ChAoS Overlord on 2005-07-06
I am planning to replace the switches with gigabit. But my question was actually about the installation procedure on linux. Since I started out with a 100 mbit and everything is configured for that NIC, would it automatically adapt these settings for my gigabit NIC or do I have to go through tedious scripts, config files & installation routines?

---

### Post by latino on 2005-07-10
Hi,

I just tried to install my Level1 Gigabit card on Ubuntu 5.04 but it just wont work :-s

keeps on getting errors about non excisting maps etc
'error 1'   'error 2'  'nothing 2 do for modules' ...

like it's not the right driver/makefile for this kernel

I'm very noob and a bit out of options so.... HeLp

Mr CTG Overloard: hoe lang moest die gigabit UTP kabel zijn?

Greetings

Z

---

### Post by Nolgthorn on 2005-07-11
My mistake I was commenting on the "Gigabyte" brand name. :roll:

---

