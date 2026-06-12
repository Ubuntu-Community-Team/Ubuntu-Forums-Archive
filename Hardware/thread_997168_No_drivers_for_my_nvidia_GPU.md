---
title: "No drivers for my nvidia GPU?"
date: 2008-11-29
forum: Hardware
---

### Post by Fzang on 2008-11-29
tl;dr:
no linux drivers for my 9650M GT, am I screwed?

I'm getting a laptop with a 9650M GT GPU and I'm planning to install linux on it...

However, nvidia doesn't seem to have any drivers for any of the GeForce 9 M series and writes that sometimes the laptop gpu driver should come from the manufactur. The manufacturer of my laptop does have drivers for my gpu but they're only for windows...

Am I screwed? Or does ubuntu include some "generic" drivers or something that will use my card? The manufacturer even states "support for ubuntu 8.04 with the exception of webcam. Nvidia CUDA works with linux"

What?? CUDA works but they don't have a driver for my gpu? How exactly does that work out?

---

### Post by doas777 on 2008-11-29
have you tried envygtk? it helps you install nvidia drivers. 

I have 2 laptops with nvidia m cards and the System -> Administration -> Hardware Drivers has had a driver for both of them.

---

### Post by Fzang on 2008-11-29
Well, I have to wait 2 weeks for the laptop to arrive so I haven't really had time to check out anything... I'm just nervous that I'm getting a laptop which doesn't support 3D on linux... :(

---

### Post by damis648 on 2008-11-29
Ah, well in that case it should definitely work. I think some 9 series have had some troubles, but they all should work, and so should yours. When you install Ubuntu, just check the Restricted Drivers Manager (System>Administration>Hardware Drivers) and check the box, you should be good to go!:popcorn:

---

### Post by Fzang on 2008-11-29
I sure hope so! Waiting 2 weeks + homework for a computer is damn hard! :|

---

### Post by doas777 on 2008-11-30
Good luck, sir. I'm hopeful it will all work out.

computing is an intelectual process, and thus takes much research, but if you have a love for it, it really pays off!

have fun, and let us know how it works out,
franklin

---

### Post by inigomontoya on 2008-11-30
This is the readme of the absolutel latest beta nvidia drivers 180.08, [ftp://download.nvidia.com/XFree86/Linux-x86/180.08/README/appendix-a.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.08/README/appendix-a.html)

I do not see the 9650M GT, i do see the 9650M GS, what is the difference?  Have you tried the 180.08 betas?

---

### Post by AllenGG on 2008-11-30
FZ, no reason that the NVidia cards will not work out of the box on Intrepid, 8.10.
Recent install :NVidia GeForce 9800GT, OOB. up and on the net in 12 minutes.
Recent upgrade : NVidia GeForce 5700LE , OOB a little tweaking
Laptop; some sort of cheapie NVidia (Acer) OOB.
WATCH carefully as you do the install. !!!

---

### Post by Fzang on 2008-12-01
Sorry but uhh... OOB?

So almost every nvidia card should work out of the box either instantly or through restricted drivers?

---

### Post by MorphiusFaydal on 2008-12-02
OOB means Out Of Box... Meaning it worked right off, with no special tricks required.

But the official nVidida drivers should work for the 9-series mobile chips as well, and they're installed through "restricted".

---

### Post by Fzang on 2008-12-02
Thanks, now I can finally sleep with peace in mind :D

---

### Post by rommert on 2009-06-04
I have a Zepto Nox A15 with 9650M GT gpu here. Can someone please verify that they got this gpu working with Ubuntu? And if so, whether they needed to do additional steps after standard install to get it working?

tnx in advance :)

---

### Post by Fzang on 2009-06-04
Revive post eh

On my Zepto nearly everything works out of the box

-9650M GT works after you update and it downloads the driver
-Intel wifi works out of the box
-Sound works out of the box
-Hibernate doesn't work out of the box but can be enabled with this guide: [http://forums.linuxmint.com/viewtopic.php?f=42&t=18346](http://forums.linuxmint.com/viewtopic.php?f=42&t=18346) (works for ubuntu as well)

Sleep doesn't work though, but that's a common problem with most laptops in linux, so you shouldn't worry

Go for it!

---

