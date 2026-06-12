---
title: "Ubuntu Intrepid 8.10 Freezes on startup"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by timshim on 2009-04-05
Hi

I have recently ugraded from 8.04 to 8.10 Intrepid. When i try to load 8.10 my screen freezes and i cant do anything, this happens just before you enter the username and password. i can only access the file system using the recovery mode boot option which isnt ideal. I dont really want to wipe ubuntu because i dont currently have a way of getting all the information off the broken version. 

The computer I am using is a 

Shuttle XPC Barebone SK22G2

Which has a:
VIA DeltaChrome 128-bit 2D/3D graphics engine

Thanks

Tim

---

### Post by cyroul on 2009-04-06
Hello,

I have the same issue at the moment, I haven t tried to fix it yet but just log in into a TTY (CTRL + ALT + F1 for example) and kill the X server and start it again, and it works again
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

Hope it will help you for now

---

