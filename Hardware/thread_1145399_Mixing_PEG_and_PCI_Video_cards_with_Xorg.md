---
title: "Mixing PEG and PCI Video cards with Xorg"
date: 2009-05-01
forum: Hardware
---

### Post by Hichhiker on 2009-05-01
I am trying to set up a 3 monitor system.

2 monitors on PEG Nvidia card and 1 monitor on old school PCI 3dfx card

I cannot seem to get them to work at the same time. 

I hand edited the xorg.conf file to include both video cards. I can get either one of them to work *without changing the xorg.conf file* if I simply pick that card in BIOS (Primary video card is PEG vs PCI option) - however when I do, no matter what I do with xorg.conf, I cannot get the *other* card to work. I am guessing something in the kernel is not loaded at boot time.

In Xorg.0.log, I can see that the server sees both cards in the beginning, but if I disable the primary device configuration, it just ends with "No devices detected."

I must be missing something simple here, any ideas?

Thanks.

-HH

---

### Post by Hichhiker on 2009-05-01
Well, I got a bit further with this, but then run into a wall. Basically Linux is just not capable of doing what I want right now - not without sacrificing something along the way. 


To get it to work I had to manually load both drivers into kernel at boot, and then provide the PCI BusIDs for each card. But even after that things were a bit screwy.

There are two ways of configuring my setup - set it as 3 separate displays and xinerama them together or use TwinView on nVidia and Xinerama it with the 3dfx card. 

In the first case it works, but there are a lot of issues with cursor being trapped in one of the screens, or multiple coursors appear (one in each display), or cursor starts leaving artifacts when moving between nvidia displays. There two nvidia displays are just not happy.

In the second case things look better, but the two nvidia displays fuse together. This is happening because instead of nvidia's xinerama extension, the system now uses the Xorg's - which cannot get the proper info from nvidia driver. There are a number of hacks for this , but they all involve re-compiling xorg and I have not found a patch newer than Xorg 1.3 (current is 1.6).

I was almost ready to try it, but then the final blow came. I could not get compiz to work under any of those scenarios.  

At this point I am officially giving up on this, unless someone has a better idea. I might look into running a completely separate X server on the 3dfx card, but I am not sure how usefull this will be.

-HH

---

