---
title: "Graphical artifacts all over the screen, can't install proprietary drivers"
date: 2012-09-08
forum: Hardware
---

### Post by rectec794613 on 2012-09-08
Hello. I have an ATI Radeon 6750 GPU running on the open source *xserver-xorg-video-ati* drivers. 

I recently did a fresh install of Ubuntu 12.10 beta 1 64bit. I know it's a pre-release version, but hear me out. To make a long story short, I have graphical artifacts all over the screen.

These artifacts seem mostly stationary. As I'm typing now, only a few seem to move at a time. However, if any new area is painted, new artifacts of a different color will appear. I won't go too in depth about the characteristics of the artifacts, because that's not very important.

The thing is, I had this same problem on 12.04 with the open source drivers, so please don't think it's just because I'm running 12.10. I fixed that problem by installing the proprietary drivers, but I can't install them on 12.10 because of unmet dependencies. My old install is semi-broken and it's only getting worse. I really don't want to have to install Precise again because I just installed Quantal and it's going to be released in just over a month anyway. 

Just to be clear: it may look hardware-related but it's not hardware-related. (I know I posted in the hardware section. Sorry if it's the wrong one for this type of problem.) The card is not overheating, and I've not overclocked it. The card is fine. 

The following screenshots are illustrations of my problem. I think it'll be much more helpful than just me trying to describe it. What do you guys make of it? All help is appreciated. Thanks.

---

### Post by Xanthius on 2012-09-08
> **rectec794613 said:**
> MY old install is semi-broken and it's only getting worse. I really don't want to have to install Precise again because I just installed Quantal and it's going to be released in just over a month anyway. 

Just to be clear: it may look hardware-related but it's not hardware-related. (I know I posted in the hardware section. Sorry if it's the wrong one for this type of problem.) The card is not overheating, and I've not overclocked it. The card is fine.

That is a little contradictory, if able please run a video memory scan as this sounds and looks kinda as a hardware failure. It does not have to do anything with overheating, it might just be a memory failure as it can happen on your RAM as well. That only has greater implications.

---

### Post by rectec794613 on 2012-09-08
> **Xanthius said:**
> That is a little contradictory, if able please run a video memory scan as this sounds and looks kinda as a hardware failure. It does not have to do anything with overheating, it might just be a memory failure as it can happen on your RAM as well. That only has greater implications.

I understand why you think it's a hardware failure, but it isn't. It's related to the xorg drivers. I could go into Windows right now, take a screenshot, and post it here. But I'm right in the middle of setting up my newly installed system right now, so you just have to trust me on this one.

EDIT: actually, no. I'll come back with a screenshot in a little bit.

---

### Post by rectec794613 on 2012-09-08
Here. This is my WIndows install. Notice that there are no artifacts. Same PC, same hardware, same GPU, etc. It's a software problem. More accurately, I think it may be incorrect usage of the hardware by the software.

---

