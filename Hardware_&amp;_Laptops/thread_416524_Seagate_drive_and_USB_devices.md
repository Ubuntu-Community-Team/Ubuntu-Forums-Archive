---
title: "Seagate drive and USB devices"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by Chxta on 2007-04-21
Feisty isn't seeing my external hard drive (Seagate 320GB), neither is it unmounting my flash disk. I have to do both from the terminal.

How am I going to convince my fiancee to make the move from Window$ when she comes to visit in June?

EDIT: My laptop is an Acer Aspire 1640Z, and I have reverted to Edgy for the time being.

---

### Post by EnigMattic on 2007-04-21
I too have a Seagate 320GB external drive. Same problem.
Out of interest, how do you manage to mount it manually from the terminal? I don't know how to do it :(

---

### Post by SodiumKPump on 2007-04-21
Hi, I have a 200 gb Seagate USB drive and I can't see it either though I can access my USB flash drive.  How do I mount it from terminal? thanks!

---

### Post by SodiumKPump on 2007-04-21
I figured it out.  

sudo fdisk -l

to find the device and then

sudo mount /dev/devicename /media/dirfordevice

Yay, noob power!

---

### Post by EnigMattic on 2007-04-21
Superb ;-)...
Just tried it, though. Didn't work for me

---

### Post by FrancoNero on 2007-04-21
I have a 160Gig external seagate and it works flawlessly I have to say

---

### Post by EnigMattic on 2007-04-21
> **FrancoNero said:**
> I have a 160Gig external seagate and it works flawlessly I have to say

Can't help noticing you're not using Feisty, matey.

---

