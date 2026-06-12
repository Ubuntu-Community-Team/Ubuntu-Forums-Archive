---
title: "Should I buy NVIDIA or AMD/ATI for Linux support?"
date: 2010-10-30
forum: Hardware
---

### Post by dr_pressure on 2010-10-30
Hi folks,

Building a new PC here, and the last component to be decided is the video card. From my research on the net it seems that the general consensus is that NVIDIA is best for Linux -- is this correct?

I'm choosing between:

NVIDIA GTX 460 1GB
AMD Radeon 5850
AMD Radeon 6870
AMD Radeon 6850

Linux support is more important to me than small differences in the price/performance of these cards, so I would really appreciate some info on how these cards do with linux.

My key requirement is that the card works out of the box on a new Ubuntu install, and that the open source drivers are stable and do not cause the system to lock up.

My understanding is that there are open source drivers available for (all?) these cards... but that all of them require proprietary drivers to do anything other than the basics. Would appreciate info on how stable the proprietary drivers are, although I may not end up using them.

Thanks in advance, much appreciated!

---

### Post by cascade9 on 2010-10-30
> **dr_pressure said:**
> NVIDIA GTX 460 1GB
AMD Radeon 5850
AMD Radeon 6870
AMD Radeon 6850

Linux support is more important to me than small differences in the price/performance of these cards, so I would really appreciate some info on how these cards do with linux.

My key requirement is that the card works out of the box on a new Ubuntu install, and that the open source drivers are stable and do not cause the system to lock up.

My understanding is that there are open source drivers available for (all?) these cards... but that all of them require proprietary drivers to do anything other than the basics. Would appreciate info on how stable the proprietary drivers are, although I may not end up using them.!

The main difference between the open source drivers and the proprietary drivers is 3D performance (gaming, etc) and a few extra features (like nvidia VDPAU and ATI XvBA). 

If your planning on running the open soruce drivers, then all those cards are pointless, they are all pretty much 'gamers cards' and I dotn klnow any gamers who run the opensource drivers. A cheaper, lower spec card will work on the dekstop just as well as the more expensive gamers cards (and use less power and create less heat into the bargin).

---

### Post by realzippy on 2010-10-30
...mods will move this to recurring or merge with e.g. :

[http://ubuntuforums.org/showthread.php?t=1511514&page=1](http://ubuntuforums.org/showthread.php?t=1511514&page=1)

You might get different answers...
I will start:

Nvidia.

---

### Post by coffeecat on 2010-10-30
> **cascade9 said:**
> The main difference between the open source drivers and the proprietary drivers is 3D performance (gaming, etc) and a few extra features (like nvidia VDPAU and ATI XvBA). 

If your planning on running the open soruce drivers, then all those cards are pointless, they are all pretty much 'gamers cards' and I dotn klnow any gamers who run the opensource drivers. A cheaper, lower spec card will work on the dekstop just as well as the more expensive gamers cards (and use less power and create less heat into the bargin).

+1 to all that. @dr_pressure, are you a gamer? That's the most important question. 

If you are then, as a generalisation, nvidia might be a better choice. But if you're not, and only want some 3d acceleration for compiz and eye-candy, then the ATI open-source driver is more able (for many cards) than the open-source nouveau driver for nvidia cards **at the moment**. In fact I moved from a nvidia card because of issues with the proprietary driver to ATI so that I could use the open-source driver - which is more than enough more for me. I chose a Radeon HD4350, which bears out cascade9's point about lower spec cards. Another bonus for me is that mine is passively cooled = SILENT. But if you choose ATI, research your chipset first. ATI seems to be more of a lottery that nvidia.

---

### Post by dr_pressure on 2010-10-30
@cascade9 Yes, I'm aware they're gaming cards. I will be using it to play games under windows, but also want it to work well on my linux partition.

@realzippy Cheers for the link

EDIT (cross-post):
@coffeecat
Thanks for the input. I'm also reading a lot of good things about nvidia in the thread zippy linked to. That makes my choice pretty easy.

---

### Post by cascade9 on 2010-10-30
OK, that makes perfect sense then, if your gaming under windows. ;) 

I'd probably go for the GTX460, though to be honest I'm not that up on the open source drivers for nvidia, I always use the proprietary drivers (for VDPAU). coffeecat probably has much better idea of the difference between the ATI and nVidia open soruce drivers, and from what coffeecat said, you might be better of with ATI if you want to run opensource drivers. 

BTW, there 2 versions of the GTX460- 768MB and 1GB/2GB. The 768MB cards are 192bit, the 1GB/2GB 256bit. The 1GB/2GB models also have more render output units (24 for 768MB, 32for 1GB/2GB). So the 1GB/2GB models are a fair chunk faster.

---

### Post by coffeecat on 2010-10-30
> **cascade9 said:**
> coffeecat probably has much better idea of the difference between the ATI and nVidia open soruce drivers, and from what coffeecat said, you might be better of with ATI if you want to run opensource drivers. 

This is theoretical because the OP wants to game and needs the proprietary driver, but as of Maverick, the ATI open source driver gives you adequate performance for compiz so long as you have an ATI card that is supported for 3d. Not all are. In fact I get good compiz in Lucid with my particular ATI card.

With nouveau and Maverick, you don't get 3d out of the box, but you can get it if you install the package libgl1-mesa-dri-experimental, but how stable that is I don't know. I tried it briefly - it worked - I moved on.

I believe from what I've read that the version of the nouveau driver that will come with Natty/11.04 will support 3d. We shall see.

Anyway, all rather off-topic for the OP.

---

### Post by cascade9 on 2010-10-30
> **coffeecat said:**
> This is theoretical because the OP wants to game and needs the proprietary driver, but as of Maverick, the ATI open source driver gives you adequate performance for compiz so long as you have an ATI card that is supported for 3d. Not all are. In fact I get good compiz in Lucid with my particular ATI card.

Unless I've made a mistake, the OP wants to run windows for gaming and the open soruce drivers for linux.

---

### Post by realzippy on 2010-10-30
Read a lot about the good compiz performance of the new fglrx river in
the last weeks here in the forum.
Can someone with a good ATI card and fglrx driver tell me:

Does FSAA and AF work (eg,16x)?(hate steps on the cube..)
Can you set a 5 mb skydome image?
Can you watch HD movies?
Windows behaviour & cube rotation is real snappy?
OpenGL fast?
Flashfullscreen fine?

I *really* would like to know this,my next card might be an ATI since
I have the idea that the image quality seems to be better in windows/gaming,but a friend runs a 4850/fglrx/Lucid,and the over-all performance is a bit poor-compared to my old 9800GTX in linux.

---

### Post by dr_pressure on 2010-10-30
Yep cascade9 is quite right. I'll be doing all my gaming on my windows partition, so probably wont need 3d for linux.

Just so long as the open source drivers are going to be stable (seems like they are) I'm satisfied. If the binary drivers are also stable then that's a definite plus.

Cheers guys

---

### Post by coffeecat on 2010-10-30
> **cascade9 said:**
> Unless I've made a mistake, the OP wants to run windows for gaming and the open soruce drivers for linux.

I stand corrected. Thanks. I made an assumption that the OP might want to game on both platforms.

---

### Post by cascade9 on 2010-10-31
You might have assumed it, but I dont think its that much of a jump.

If dr_pressure found a game that ran under linux (whatever distro) as well as windows, then playing under linux makes sense. IMO anyway.

---

### Post by P4man on 2010-10-31
Rule of thumb 1: OSS drivers are better for ATI, proprietary driver support is (a lot) better for nVidia.

That rule of thumb may not apply to the newest ATI cards, I thought the OSS drivers still often struggled with the HD5x cards, I would be surprised if their were no issues with the HD6x cards. They do work fairly well with older cards though.

Rule of thumb 2: for linux, stick with nvidia when at all possible.

---

### Post by cromat on 2010-11-11
I'm going to disagree with you, I am running Ubuntu 10.10 and enabling the proprietary driver. I have a ATI HD5870 running 3 monitors (eyefinity in windows) and other that games under linux no issues.  I can even have the 3 monitors running off the one card.  ATI is consistently working on new drivers now and for the upcoming switch to wayland ATI is already in a better position for the switch due to how the driver works. Nvidia on the other hand has  flat out said "We will not support wayland".  Food for thought....

---

### Post by P4man on 2010-11-11
One nVidia guy said 'we have no plans to support wayland'. And at this point, why would they? We are probably 4-5 years from seeing wayland adopted by ubuntu or any mainstream distro, if it will ever happen. Perhaps you can show me a link where AMD does state they will support wayland?

As for the current drivers; Im glad it works for you. I have very different experience with my 4870. Screen tearing and flickering with compiz and playing flash. No h264 decode acceleration. Unity not working at all (works fine when I plug an nvidia card). Multi monitor support is a joke. Seriously. I mean its great a card thats supposed to support three monitors actually supports three monitors. Meanwhile with my 2 monitors I cant even change resolution without rebooting. Dissimilar size monitors is messed up. I cant set a primary monitor without fiddling in xorg.conf. I cant hotplug monitors properly. I cant check my GPU temperatures in either catalyst or lm-sensors. I cant change power management profiles. I could go on.

I agree they are improving but they are still miles away from the level of nvidia's restricted drivers.

---

### Post by Zero Prime on 2011-05-10
I will never understand what all the fuss is with ATI.  I've used both an ATI 4670HD and now a 4250HD in my laptop.  The restricted drivers work great.  I have awesome 3D and 2D performance.  Hy HD output to the TV works flawlessly with both video and audio.  I actually switched to ATI after so many complications with my last Nvidia card.

---

