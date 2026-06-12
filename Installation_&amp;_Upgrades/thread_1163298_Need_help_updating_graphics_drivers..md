---
title: "Need help updating graphics drivers."
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by Venter127 on 2009-05-18
After downloading Cube 2, I realised the game-related programs installed on my ubuntu OS tend to run at about half the speed of the programs in my Vista OS, and frequently crash. I even ran an emulator through Wine, and it ran somewhere between 20-30 frames per second during gameplay, whereas I can get a solid 60 running it on vista. This strikes me as confusing, since both operating systems are running off the same hardware, so how does the software make it run so slow?. When I asked for a solution in a forum, I was suggested to update my graphics drivers for Ubuntu (Which I had not previously done). Running the hardware drivers app from the Admin. tab didnt do anything to help me, so I looked it up on the internet. After about an hour of searching, I found A site (Namely, this one:_ _[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)) with the driver update I needed, but Im a little confused as how to proceed installing them. I am still (very) new to the workings of linux, so I dont want to do anything that would jepordize my system.

My graphics card is the "Intel G45 Express Chipset," and when I go to the downloads page, Im given 4 options:
1) X.org 2D driver
2) Mesa 3D GL driver
3) DRM and AGPGART kernel module
4) LIBDRM userland DRM module

Each one gives me some form of code Im unfamiliar with, and this is where I get confused. What am I supposed to do with this code to get it to install? Do I need all of these drivers, or just one, and if so, Which one should I get?

Also, If theres anything else I can do to improve the performance of my programs in Ubuntu, please let me know.

Any help would be greatly appreciated.

---

### Post by Mark Phelps on 2009-05-19
> **Venter127 said:**
> I even ran an emulator through Wine, and it ran somewhere between 20-30 frames per second during gameplay, whereas I can get a solid 60 running it on vista. This strikes me as confusing, since both operating systems are running off the same hardware, so how does the software make it run so slow?. 

You've basically answered your own question.  Any SW emulation is going to cost CPU cycles, which will result in some performance loss.  Also, in Vista, you're probably using video drivers that incorporate hardware acceleration.  If your Ubuntu driver do not do that, Ubuntu's performance in 3D will be a lot slower.

> My graphics card is the "Intel G45 Express Chipset," and when I go to the downloads page, Im given 4 options:
1) X.org 2D driver
2) Mesa 3D GL driver
3) DRM and AGPGART kernel module
4) LIBDRM userland DRM module

Each one gives me some form of code Im unfamiliar with, and this is where I get confused. What am I supposed to do with this code to get it to install? Do I need all of these drivers, or just one, and if so, Which one should I get?

I don't have a machine with the Intel G45 chipset, but I've seen bunches of posts on the forums about problems people have had with intel chipsets after 9.04 upgrades and installs.  Sorry, can't help you there.

---

### Post by Venter127 on 2009-05-20
Thanks for the info, but Im not quite sure its a problem with WHAT I need to download, I think im just having a hard time trying to figure out HOW to install it. After looking through the Ubuntu pocket guide, It looks like I need to work with some reposotories here, but when I try to add the code it gives me, It doesnt let me add it, so there must be something im doing wrong. I think there are a few problems, and anyone who has done something like this before, I would be eternally grateful if you checked the site of the drivers, and showed me how to to get it to run.

I think ONE of the reasons I cant install anything is because it uses some kind of file extension ive never seen before. Whenever Ive seen a repository being added, they always typed "deb" infront of the address, whereas all the code I see on the website has "git" in front of it.

---

