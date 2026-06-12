---
title: "Ubuntu 8.04 Doesn't Recognize my NVIDIA Graphics Card"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by jvargas on 2009-02-21
[COLOR="Navy"]I've combed through google searches and forums but I can't find a concrete answer to my issue. 

I have a EVGA NVDIA 9600GT grphx card. After installing Hardy Heron, I get a black screen upon boot up. I have no onboard video to plug into and see if I can upgrade my video drivers some way or another. I've tried using a newer version of Ubuntu but it still does the same thing. I should also mention that I have a dual-screen going on but I'm not sure if that's the cause of my issue. Any help would be appreciated. Thanks!


My Specs:
ASUS P5QL
Intel C2D E8400 3.0Ghz OC 3.83GHz
8GB RAM
EVGA NVIDIA 9600GT 512MB
160GB SATA HDD(Primary)
500GB SATA HDD(Slave)



[/COLOR]

---

### Post by lemming465 on 2009-02-22
If you boot in rescue mode (single user), do you get a text console, or is it still black screen?  Do any live CD's do video?  Can you get to /etc/X11/xorg.conf and specify *Driver "nv"*?

---

### Post by Mark Phelps on 2009-02-23
I could be wrong here, but I tried dual-screen in Hardy and it didn't work.  I believe that Intrepid may be the first Ubuntu distro to handle multi-screen by default.  

Anyway ... would disconnect one screen and see what success you have using a single screen.  You can always add the second screen later, once you get Ubuntu up and running.

---

