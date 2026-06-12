---
title: "Ubuntu Mobile Internet Device / GeForce Go 7600"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by balddogger on 2009-03-20
I have Ubuntu MID (ubuntu-8.10-mid-lpia.img) up and running on my custom hardware (Intel Core2 Duo, 2gig USB Flash, NVIDIA G73M GPU).  

Next is to get the nNvidia-glx drives up and running.  This is where I can use some help.

Looks like I have a few options, but nothing seems to be working.
1) Synaptic fails do to the kernel name (can't find the corresponding repository).
2) The Nvidia installer (NVIDIA-Linux-x86-xxx-pkg1.run) also fails to download the driver itself, due to the "lpia" kernel
3) The Nvidia installer tries to complie the driver from source, but I only have a 2gig USB drive.  So, there is not enough space to do this.  

Any thoughts?

My custom hardware does have a USB port, I could buy a large thumb drive, compile the driver on that.

---

### Post by balddogger on 2009-03-24
bump

---

### Post by asktomcat on 2009-04-02
sorry i don't have any advise but i am curios as what path you take and how it turn out 

any update on your MID project is appreciated
thanks

---

### Post by balddogger on 2009-04-13
asktomcat - I ended up installing Ubuntu MID on a USB Thumbdrive (persistent) and installing the Nvidia graphics drivers from source using Nvidia's install program (downloads source and complies).  

So, know I just need to copy what I need from the thumb drive to my onboard flash.  

Looks like the window manager for MID doesn't like when you have 3 or more applications running...

---

