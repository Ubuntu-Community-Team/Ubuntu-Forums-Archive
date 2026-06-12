---
title: "New system, Chrome video a mess, alternatives?"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by ladasky on 2009-09-05
Hi folks,
 
I just inherited a hand-me-down computer.  The good news is that its fairly new.  The bad news is that when I booted from the Ubuntu 8.04 LTS 32-bit x86 Live CD, the video went to pieces once the desktop appeared.  
 
Diagonal stripes and hash were everywhere, there was ghosting, etc.  If there is interest in the details, I will post a photo.  Reading anything but the simplest text was impossible, and I could barely maneuver the mouse over the shut-down icon.
 
The motherboard in this system is a **[model P4M900T-M (V1.0) from ECS]("http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?detailid=704&CategoryID=1&DetailName=Specification&MenuID=1&LanID=0")**.  The on-board video, which I was trying to use, is described as "Integrated Chrome9™ HC IGP".  
 
Since Chrome9 video is apparently not widely used, it appears that support for it is limited.  I found **[this discussion]("http://ubuntuforums.org/showthread.php?t=485646&highlight=chrome9")** of **[OpenChrome]("https://help.ubuntu.com/community/OpenChrome")**.  Maybe I would be among the roughly 50% of people who reported that OpenChrome solved their problems.  HOWEVER, installing and configuring it involves opening a terminal and doing a fair amount of typing.  To do that, I would actually need to be able to read the screen!

In **[this recent discussion]("http://ubuntuforums.org/showthread.php?t=1257595&highlight=chrome9")**, a fellow Ubuntu user says to forget Chrome and just buy another video card.  Since I was eventually planning to do this anyway, I was thinking that I might just do that now.  I am considering some of the cheaper CUDA-equipped cards from NVidia, as I do a lot of computation.  Are NVidia outboard video cards a good bet for working right out of the box, or can I expect more problems?
 
Thanks for your input!

---

### Post by ladasky on 2009-09-06
Following up to my own post...
 
It seems like a bit of a violation of the Linux spirit, which implies that any problem can be solved with a little ingenuity and patience.  But I went ahead and purchased an NVidia 9400 GT video card, the cheapest one my local computer store had which included CUDA.  It worked straight out of the box, and I don't have to fuss with Chrome.
 
So, I solved by problem by going around it. :?

---

