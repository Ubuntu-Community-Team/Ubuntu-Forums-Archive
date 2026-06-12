---
title: "Which graphic card to buy? ATI vs Nvidia"
date: 2010-08-08
forum: Hardware
---

### Post by benplanet on 2010-08-08
Which has the best LINUX support? Nvidia or ATI ? I am looking to upgrade from an old 7800GT to a HD5870 ATI card... what do you recommend? any issues with linux 64bit catalyst drivers? should I just stick with nvidia? or worse, downgrade to windows 7? :p kidding. 



thanks!

---

### Post by cascade9 on 2010-08-08
Game much? I really hope so, or else a 5870 is wayyyy overkill. 

Fom what I've seen, there tends to be more issues with ATI drivers than nVidia drivers, but I dont know if I'd get an nVidia card at that price-point...the GTX4XX cards are very power hungry and hot. You might need to upgrade power supply to run a GTX4XX. The ATI cards use a lot less power and are cooler.

---

### Post by benplanet on 2010-08-08
> **cascade9 said:**
> Game much? I really hope so, or else a 5870 is wayyyy overkill. 

Fom what I've seen, there tends to be more issues with ATI drivers than nVidia drivers, but I dont know if I'd get an nVidia card at that price-point...the GTX4XX cards are very power hungry and hot. You might need to upgrade power supply to run a GTX4XX. The ATI cards use a lot less power and are cooler.

exactly my thought, nvidia runs way too hot and consumes more power. I plan to play some first shooter, NOT MUCH tho. Mostly it's for video editing and running large multi-monitor setup. Would I be okay with a 5850?

---

### Post by krishnandu.sarkar on 2010-08-08
Of course  HD5870, but as others said ATI has some serious driver problems with Ubuntu.

---

### Post by cascade9 on 2010-08-08
From what I know, video editing isnt helped that much, if at all, by GPUs. 

You might do better to find a CPU and/or RAM upgrade and going for a slower video card, like an nVidia GTS 250 or GTX260, or an ATI 5670 or 5770. (The GTX260 is probably not the best choice in some ways, they are almost the same price as a GTX4XX). 

The GTS250 should give you a nice boost over the 7800GT, and leave you a nice chuck of money for a CPU and/or RAM upgrade.

---

### Post by S.R on 2010-08-08
I am running dual 5770's. The driver was not to big of pain to get squared away.

---

### Post by penguin7009 on 2010-08-08
Hi all, running Alienware m17x r2 with ATI 5870 x 1gig single card.  The catalyst control center and fglrx drivers from the repositories all worked from the getgo.

The drivers are not good enough to play hard core games but for everyday work and 2d graphics they are fine.  There is some double loading and flashing when booting but the extended built-in graphics worked after the upgrade to the ati drivers.

Havent tried compiz but enabling the highest graphics setting through look and feel settings produces a nice set of 2d graphics including wobbly windows and such.

As far as which card to buy, Nvidia is better supported and the drivers are much better, but that is changing.

glxgears output:

Ati 5870m x 1 gig=1389 fps
Nvidia gt260m 1 gig=7289 fps
Hope this helps.

penguin

---

### Post by PresenceofMind on 2010-08-08
> **benplanet said:**
> Which has the best LINUX support? Nvidia or ATI ? I am looking to upgrade from an old 7800GT to a HD5870 ATI card... what do you recommend? any issues with linux 64bit catalyst drivers? should I just stick with nvidia? or worse, downgrade to windows 7? :p kidding. 



thanks!

Yo!!!

Haha.... 5870 is a HUGE leap from a 7800 GT. But I can't recommend anything unless you tell me what you want to use your card for :P

On the driver-side of things.... I prefer NVidia.

---

### Post by penguin7009 on 2010-08-08
> **PresenceofMind said:**
> Yo!!!

Haha.... 5870 is a HUGE leap from a 7800 GT. But I can't recommend anything unless you tell me what you want to use your card for :P

On the driver-side of things.... I prefer NVidia.


I have always preferred Nvidia cards because of the support they have of Linux.  Problem is the Linux drivers do not support anything in sli or crossfire.  Each time one reboots one has to go into the Bios and reset the cards to off and then reboot, a big pain. The cards can be configured to work in sli/crossfire but its a big pain and not worth the effort-my opinion.

The Linux drivers for Ati, right now, are not as good as Nvidia (see the difference in frame rates) but that is changing fast since AMD has taken over.  

penguin

---

### Post by S.R on 2010-08-10
> **penguin7009 said:**
> Problem is the Linux drivers do not support anything in sli or crossfire.  Each time one reboots one has to go into the Bios and reset the cards to off and then reboot, a big pain. The cards can be configured to work in sli/crossfire but its a big pain and not worth the effort-my opinion.

The Linux drivers for Ati, right now, are not as good as Nvidia (see the difference in frame rates) but that is changing fast since AMD has taken over.  

What??? I have had zero problems with install of drivers or crossfire. SLI has had Linux support since 2005 and Crossfire support started with the Radeon HD 4800. That is not saying every card will work with no trouble but a little research can go a long way especially when making recommendations. 

It is equally important to make sure that the GPU selected will work well with the chosen motherboard.

Reference siting: August 2008 blog/article [http://www.phoronix.com/scan.php?page=article&item=amd_crossfire_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_crossfire_linux&num=1)

---

### Post by Zorgoth on 2010-08-10
I don't know if Linux drivers are out yet but GTX 460 is the best card for the money right now.

---

### Post by SeePU on 2010-08-13
I am still not convinced that ATI is a viable alternative for a graphics card in Linux.  In fact, it's a poor choice.  ATI doesn't seem to want to support Linux despite having an open source option.

There's tons of issues even with HD 4xxx cards.  The 3D/2D features in the binary driver are plaqued with problems.  If you have to use the open source radeon driver, you are limited regarding features.  

Using an ATI card to watch movies or do anything with video, you encounter issues like tearing and worse.   There's no hardware acceleration.  Remember, if you are buying a HD 5xxx card, you are spending big money but it's way more useful in Windows.  I wonder why that is.

Until I'm persuaded otherwise, I'd consider Nvidia.  The main problem with Nvidia cards right now is their newer cards are all high-grade cards so more costly.  ATI might have better hardware overall and a wider variety of choices of newer cards but ATI drivers in Linux cancel out that advantage.

---

### Post by SeePU on 2010-08-19
Sorry, I'd like to bump this thread. 

I was wondering if there's any changes.  Ubuntu Lucid 10.04 has XServer 1.8 and I think 10.10 will have 1.9.  I'm just curious what HD 5xxx owners are experiencing with their card.  

I really want a HD 5770 but deal breakers are any problems with video.  Is there still tearing?  I read that there is.  I need 3D so at least, min., GoogleEarth.  It doesn't have to do major stuff yet like CAD or something as I'm willing to wait for driver improvements in 3D.  As long as I can play tear-free video.  I read that hardware acceleration and other features aren't yet working and that's a concern, too.  ATI is notoriously slow for improvements, right?

If I go with a Nvidia card, I'd probably get a cheap card for now.  I don't need a $200+ card although I wish I could get a GTX 460.  That would be my card if I could invest over $200 in a video card.  I'm pushing it with a HD 5770 but I like how it keeps cool and is still decent with overall performance.  

If I go with an old Nvidia card, what's a good price?  I can get a 9800GT for $60 or a GT 240 for $80-$100 or a GTS 250 new for $120 (maybe used for $90 but those usually go pretty fast).  

Recommendations?  Oh yeah, keep tabs on phoronix website because the updates on the HD 5000 cards are interesting and informative.  But, it's interesting to have word of mouth here from Ubuntu users who have the cards!  User experience is still useful since they give a possible impression and idea of what to expect? :)

---

### Post by realzippy on 2010-08-19
A 9800GT will work pretty good.No need in linux
for a faster card....unless you run doom3 benchmarks.
More Video RAM enables larger compiz skydome images   ;-)

---

### Post by cascade9 on 2010-08-21
> **realzippy said:**
> A 9800GT will work pretty good.No need in linux
for a faster card....unless you run doom3 benchmarks.
More Video RAM enables larger compiz skydome images   ;-)

Will a 9800GT run all the avaible (linux native) 1st person shooters at 1920x1200 or 1920x1080 with full AA+AF? I doubt it. 

Does video RAM really have that much impact on compiz after you have a decent amount (say, 128-256MB minimum). I have no idea on this, I never use compiz. I'd be suprised if more than 256MB made any difference to compiz.

---

