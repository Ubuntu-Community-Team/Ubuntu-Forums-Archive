---
title: "New Guy All Messed up. GeForce FX 5500 and DWA 552"
date: 2008-06-05
forum: Hardware
---

### Post by rx8mep on 2008-06-05
Hello everyone,

I'm new to the ubuntu/linux scene, and my friends and I work at circuit city and they love ubuntu, so I decided I would give it a try. I have a Dell Dimension 4400 that I am currently running my ubuntu on. I have a GeForce FX 5500 graphics card, and a DLink Xtreme N Desktop Adaptor, DWA-552. My problem is I cannot seem to get anything to work.

I installed ubuntu, and got into the desktop area. I am a windows user, so I am not familiar with anything of this sort. I try to use the cool Desktop effects but they wouldn't work, so I read that you have to enable the driver. I thought, simple enough, but the driver has a check for enabled but next to it, it says not in use. I read about compiz, but everyone would say type " something / something " and I never knew where to type it. I looked around and I thought I would press Alt + F2, but it never did anything. So I put compiz on my flashdrive from my windows computer and i hit run from terminal. it started up and asked me about blacklisting, I didn't know what it was so I hit yes, but now i'm realizing that the blacklist is not good. I do not know how to get out of what i've done, so i tried recovery mode, but i still have the same problem.

A lot of things I see ask me to connect to the internet, but I cannot connect to it because of my wireless card. so i looked up how to remedy that one. well i brought the 3 files over that I was instructed to, but they will not load and I am getting a looks like a graphics card error. it says:

Status: Error: Dependency is not satisfiable: ndiswrapper-utlis-1.9

Description: graphical frontend for ndiswrapper (installation of Windows WiFi drivers)

ndisgtk is a GTK based frontend for ndiswrapper, allowing an easy way to install Windows wireless drivers.

So I can't get on the internet to help myself with my graphics card on this computer, and I can't configure my graphics card without the internet, so I'm pretty screwed. I tried to look around for similar answers to my problems, but I couldn't find one quite like my own, a lot were worst, and some weren't as bad as mine, but I'd appreciate the support. Thanks in advance.

---

### Post by aquavitae on 2008-06-05
What state is your system right now? Can you get onto the desktop? Is it working apart from the internet and graphics?

I'd say your priority is to get the internet working. You can use it without cool effects, but you're kinda crippled without the internet. 
> Status: Error: Dependency is not satisfiable: ndiswrapper-utlis-1.9
This means that in order to install the packages you have,you first need to install the packages ndiswrapper-utils-1.9 (I assume "utlis" is a typo?). Just a quick explanation of the naming system - the package name is ndiswrapper-utils and the version is 1.9. You can search and download it from [http://packages.ubuntu.com]("http://packages.ubuntu.com")

> type " something / something " and I never knew where to type it.Type it in a terminal - go to Applications, Accessories, Terminal.

---

### Post by rx8mep on 2008-06-05
My system: I can get onto the desktop, and yes it is working besides the internet and graphics. You were right about installing the different packs first before that one. Now I am following the directions to get my network card working. Thanks for the info on the terminal. Everyone was saying Terminal and I was like "ahh where is it??" :D Now I am having a problem installing cabextract and unshield, to get to my driver for my Network card. :(

---

### Post by rx8mep on 2008-06-05
ok, sweet. thank you, i got the internet working. i did a lot of reading and i finally got my dwa 552 card working. now just to get my graphics card working @.@.

---

### Post by aquavitae on 2008-06-06
If you've got the internet working, all you need to do for the graphics is install nvidia-glx-new and nvidia-new-kernel-source. But it should automatically install these.

---

