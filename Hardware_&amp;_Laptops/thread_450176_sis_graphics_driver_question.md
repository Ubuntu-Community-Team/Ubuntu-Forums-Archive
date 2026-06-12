---
title: "sis graphics driver question"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by chr3681 on 2007-05-21
I am running Feisty Fawn on my Acer Aspire 5000. I looked on the Acer site and it says I am using an SIS graphics card. I was wondering if someone could help me find and install drivers for my card. Also, I figure there are obviously different models of the SIS graphics card so is there a command or something I can run to find out exactly which one I have to help you help me better? =)

Thanks for the help!

---

### Post by teaker1s on 2007-05-21
you can find out graphics card by 
```
lspci | grep VGA
```

 to configure xserver
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by chr3681 on 2007-05-21
everything works fine with xserver i just wanted to install the drivers so i can use higher resolutions and stuff like that.

when i run lspci | grep VGA i get this:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by tturrisi on 2007-05-21
> **chr3681 said:**
> everything works fine with xserver i just wanted to install the drivers so i can use higher resolutions and stuff like that.

when i run lspci | grep VGA i get this:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

You already have the sis drivers installed!
do:
sudo dpkg-reconfigure xserver-xorg and add resolutions you want to be able to use.

---

### Post by chr3681 on 2007-05-22
wow i feel dumb lol. thanks for the help, i got the resolution i wanted up and working =)

---

### Post by bakermiller on 2007-05-31
i have the exact same card.

...i'm sure you don't have 3d acceleration....do you ? i don't :(

SiS won't release their drivers as open source. acceleration worked under windows, but just crashes my computer when i try something somewhat 3D intensive under feisty... i've been fighting with this for over one month now... i gave it up.

A super-linux-user-friend says he will fix my kernel and make it work some day. i can't wait. for now i can't run google earth or any 3D screensaver or enven | grep glx info, it just kills my computer :P

i can't wait for SiS to release their drives. I may have to complain to them that the hardware i bought from them is not compatible with the OS i CHOOSE to install.

i tried this guys SiS stuff, but it still does'nt work...

[http://www.winischhofer.eu/linuxsispart1.shtml](http://www.winischhofer.eu/linuxsispart1.shtml)

---

### Post by chr3681 on 2007-05-31
yeah you are exactly right. i try running google earth or a 3d screensaver and it just crashes. i really wish they would release those drivers!!

---

### Post by gabo on 2007-06-04
[www.winischhofer.eu](www.winischhofer.eu) driver works well with SIS, the problem is that it has drivers up to X11 7.1 and  with Feisty (at least, since I am using it) I have the 7.2 Server.

Maybe this guy will release the new driver soon.

Any suggestions? I have the same problem.

---

### Post by tturrisi on 2007-06-04
> **gabo said:**
> [www.winischhofer.eu](www.winischhofer.eu) driver works well with SIS, the problem is that it has drivers up to X11 7.1 and  with Feisty (at least, since I am using it) I have the 7.2 Server.

Maybe this guy will release the new driver soon.

Any suggestions? I have the same problem.
He's the debian sis  driver maintainer, his drivers are the ones in debian already.

---

### Post by tturrisi on 2007-06-04
The 3D limitations has nothing to do w/ the sis drivers.  It has to do with the sis chipset itself, it does not support 3D.
quote from the developer of the sis driver:
[http://www.winischhofer.eu/linuxsispart3.shtml#faq](http://www.winischhofer.eu/linuxsispart3.shtml#faq)
> Q: Tuxracer is terribly slow on my SiS 315/550/650/651/330/661/741/760/761/340/XGI Vx
A: DRI and hardware accelerated OpenGL/3D is not supported on these chipsets. I don't know how many times I must say this. And besides, I don't do any DRI related development.

---

