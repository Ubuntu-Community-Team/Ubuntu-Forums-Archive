---
title: "Installing Windows Programs"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by Lou29 on 2009-05-15
How do I install Windows programs on UBUNTU ?

---

### Post by ad_267 on 2009-05-15
First of all, Ubuntu is a lot different to Windows and isn't designed to run Windows applications. Windows applications have been compiled to run specifically on Windows.

That said, there are ways to do it. If you have a legal copy of Windows you can install it on a virtual machine in Ubuntu using VirtualBox. Or you can install a Windows compatibility layer called WINE. WINE will let you run quite a wide range of Windows applications but not all of them.

---

### Post by Lou29 on 2009-05-15
Ok I see so how about if I have to install drivers for my video card and my sound card this is my first time using this, I just heard you can use windows programs on Linux based OS'
how about if I wanna install a video game or something.

---

### Post by lisati on 2009-05-15
Like ad_267 said, Windows programs generally don't work on Linux without help. Wine will help you run *some* (but not all) programs designed for MS Windows. Have a look here: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

If it's drivers for MS Windows you want to use, then that's another story. It can be done, but I don't have the "know how" without searching the forums.

---

### Post by Lou29 on 2009-05-15
Thanx for the info  :D

---

### Post by albinootje on 2009-05-15
> **Lou29 said:**
> 
I just heard you can use windows programs on Linux based OS'

Yes, but YMMV. There's virtualisation/PC-emulation with e.g. VMware and VirtualBox in which you can have MS-Windows as guest VM, but there's also Wine, which is more of a single program loader.
> 
how about if I wanna install a video game or something.

I'm not a gamer, but for MS-Windows games inside Linux check here : [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)
See also here : [http://appdb.winehq.org/](http://appdb.winehq.org/) and here :
[http://www.codeweavers.com/products/cxgames/](http://www.codeweavers.com/products/cxgames/)
[http://frankscorner.org/](http://frankscorner.org/)

---

### Post by Lou29 on 2009-05-15
oh damn thanx for those links :D

---

### Post by ad_267 on 2009-05-15
> **Lou29 said:**
> Ok I see so how about if I have to install drivers for my video card and my sound card this is my first time using this, I just heard you can use windows programs on Linux based OS'
how about if I wanna install a video game or something.

No, you can't install Windows drivers on Ubuntu, but why would you want to? Just go to System - Administration - Hardware Drivers and you can install the drivers from the card vendor, unless you have a card that comes with open source drivers, in which case you don't have to do anything.

You can run some games on Ubuntu using Wine with varying amounts of success. The Wine [Application Database]("http://appdb.winehq.org/") will tell you how well different applications work on Wine.

Honestly though, if you're just going to want to run Windows applications and games, you're better off using Windows. If you're willing to learn something new and use the native Linux applications, which in many cases are just as good or better than the Windows counterparts, then give Ubuntu a try.

---

### Post by albinootje on 2009-05-15
> **ad_267 said:**
> No, you can't install Windows drivers on Ubuntu, but why would you want to? 

[nitpick-mode-off/generic-information-mode-for-Linux-beginners on]
With Ndiswrapper you can use MS-Windows drivers for wireless cards, and that can be very handy when there's no properly working native Linux driver available yet.

Perhaps a funny thing to know is that a similar Ndiswrapper project for FreeBSD exists, there it is known as "Project Evil" :)
For more info, see here : [http://en.wikipedia.org/wiki/NdisWrapper](http://en.wikipedia.org/wiki/NdisWrapper)

---

### Post by ad_267 on 2009-05-15
Yes I forgot about ndiswrapper, but for video/audio drivers and in general this isn't an option. And ndiswrapper is only for when there's no other option.

---

### Post by albinootje on 2009-05-15
> **ad_267 said:**
> Yes I forgot about ndiswrapper, but for video/audio drivers and in general this isn't an option. And ndiswrapper is only for when there's no other option.

Exactly. 
And my post was just meant for informing new Linux users, that's all.

---

