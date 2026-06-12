---
title: "Help geting Ubuntu 9.04 x64 working."
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by travin law on 2009-09-08
[SIZE=3]Hi every one,

I just switched over to ubuntu 9.04 about 3 weeks ago, installed ubuntu 9.04 x64, then whent about installing some of my games, when i tryed to play them i got a error saying that my system did not meet the requirement for the game, i looked around on the net for some help and found that i just had to install new drivers for my Nvidia GTX 260, so i follow a guide i found on how to do that and when my pc restarted Gnome would not start up, so i try re-installed Ubuntu and the Nvidia drivers and the same thing happend, i have reinstalled about 15 times every time trying a new help guide but i can't seem to find one that leves me with a working pc at the end of it.

At the moment I'm just running my PC on a fresh installation of Ubuntu 9.04 x64. Dose any one know where i can find help setting up Ubuntu 9.04 x64 so that my pc is not just a very expensive calculator.

**Hear is my Setup**:
Motherbord: nForce 780i 3-way SLI
CPU: Intel Core 2 Quad
RAM: 8GB
Video Cards: 2x Nvidia GTX 260
Sound Card: N/A Waiting to get Ubuntu working before buying a new one.
Moniter 01: Samsung SyncMaster 2233BW
Moniter 02: Samsung LCD 32" LA32A550P1FXXY

If any one has a simmler setup to mine or knows where to find a guide (for some one that is new to Ubuntu and linux) that has how to set up a system the same or simmler to mine then please let me know, i don't want to go back to using Windows as my primery OS.

Thanks to any one that can Help in advance.
Travin Law
[/SIZE]

---

### Post by sune_cph on 2009-09-09
I have a single GTX 260 and never had any issues in my ubuntu x64 distros (currently i use 9.10 amd64 version). I normally use the post-installation nvidia restricted drivers.

Have you tried with just a single GTX 260? Maybe it is confused about the dual cards..

Good luck,

/Sune

---

### Post by travin law on 2009-09-18
I have tried re-installing Ubuntu 9.04 amd 64 with just the one GTX 260 in the PICE x16_1 slot but i still get the same problem, is it installing the wrong default drivers? I'v tryed installing the post-installation nvidia restricted drivers but then Gnome dosen't want to start up.

Are there drivers that i need to get for my motherboard?
Any one have any segestion on how to get it working?
If it will help i can post a copy of the "xorg.con"files.

Please Help if you can,

Pleading to be saved by the gods,
Travin Law

---

### Post by aditya.gnu on 2009-09-18
dear U Geek , firstly I would like to you ask is , whether your PC supports 64 Bit OS or in other words is your processor a 64 Bit. if yes , then there should be no problem , unless you doing something extreme installation ..etc..
But if not, then its waste of installing games on the machine which has Jaunty x64 bit.

Aditya.

---

### Post by presence1960 on 2009-09-18
> **aditya.gnu said:**
> dear U Geek , firstly I would like to you ask is , whether your PC supports 64 Bit OS or in other words is your processor a 64 Bit. if yes , then there should be no problem , unless you doing something extreme installation ..etc..
But if not, then its waste of installing games on the machine which has Jaunty x64 bit.

Aditya.
all dual core & quad core CPUs are 64 bit!

---

### Post by presence1960 on 2009-09-18
Did you try using envyng to install the drivers for your Nvidia cards?

If not, boot into Ubuntu and install envyng by running these commands
```
sudo apt-get install envyng-core
``` & ```
sudo apt-get install envyng-qt
```

You can run envyng by going Applications > System Tools > Envyng or running ```
envyng -t
``` in terminal for text version or ```
envyng -k
``` for a graphical front end

---

