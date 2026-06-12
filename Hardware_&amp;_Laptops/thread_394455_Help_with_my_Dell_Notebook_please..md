---
title: "Help with my Dell Notebook please."
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by mikedeaton on 2007-03-26
I bought a Dell E1505 notebook back in October and wanted to install a new OS on it and found Ubuntu Edgy, so I downloaded it, burned the .iso and installed it on my laptop. Well, I'm completely new to Linux and know nothing about it and I can't get my wireless to work. I tried to press fn+F2 to enable the wireless and it didnt work. And when I looked at the list of my devices it doesnt even show up my wirless card. My computer specs are:

CPU: Intel core 2 duo 1.66Ghz
RAM: 1 gig
HDD: 60 gigs
Video: ATI Radeon X1300
Wifi: Intergrated wireless G/B card

Well I need help getting the card to work and using it. I also need help getting my video card to work properly. I have a fresh installation of Ubuntu and am awaiting help. Please explain it step by step in dumbance terms. :(

---

### Post by bwingbob on 2007-03-26
[This]("http://www.ubuntuforums.org/showthread.php?t=257684&highlight=dell+e1505+wireless")   looks pretty complete.

I found a couple of other references on [Google]("http://www.google.com/search?q=Dell+E1505+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") that indicated, your wireless should just work with the latest kernel. Check System->Administration->Networking and see if your wireless connection is enabled. If it is not, enable it.

---

### Post by terrigan on 2007-03-31
Ah yes, the E1505. How i know it well. *pats laptop* The problem is the integrated wireless card, Broadcom 43xx. You can follow the route that Bob outlined in his first link but I went the route using bcm43xx-fwcutter directions, big thanks to nickm for these,

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=fwcutter](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=fwcutter)

Now i'm not too sure how well they work under ubuntu or it may well be network-manager, which i've seen countless people complain about but i've noticed that i get sporadic internet slowdowns and the download plugin in Firefox maxes at 20k and bounces down to 7,000 bytes and back again. *shrug* At least it works, eh? :)

---

