---
title: "Linux vs. HDMI"
date: 2010-05-27
forum: Hardware
---

### Post by DjRedo on 2010-05-27
Hello

I just wanted to see if people are aware of the seemingly massive problems with Linux and certain HD-TVs being so incomatible that it actually ruins the TV.

Ive blown 2 TVs so far, and dare not use Linux anymore. For reference, check out this post:

[http://forums.cnet.com/5208-13973_102-0.html?messageID=3186416&tag=mncol;lst;9#3186416](http://forums.cnet.com/5208-13973_102-0.html?messageID=3186416&tag=mncol;lst;9#3186416)

There are many more if you google Linux/HDMI/tint

I guess this could very well be the TVs that are using crappy HW, but its still an issue. The last repairman I spoke to said he strongly recommended not using Linux. (and dont bother to post comments about not using this and that TV, the point is that if TV vendors start saying Linux might mess up your TV its not a good thing, no matter who's to blame).

From the number of posts Ive found on the net about this, its a major issue. Anyone know about any possible solutions, or am I stuck with Bill as long as I have this TV?

All input appreciated. Tyvm.

---

### Post by Jakiejake on 2010-05-27
I don't think that's right
Just Sayin...
Just because some people don't like Linux... :confused:

---

### Post by Sub101 on 2010-05-27
Works fine for me on 2 different Panasonics.

Based on the posts you have linked to does the VGA connection work?

---

### Post by DjRedo on 2010-05-27
> **Sub101 said:**
> Works fine for me on 2 different Panasonics.

Based on the posts you have linked to does the VGA connection work?

Thanx for posting.

Just for clarity: I'm not saying it doesnt work for **any** HDMI. But it seems to be alot of cases. And when the guy told me I should stay clear of Linux since he had seen many cases of the same, I thought it was worth a post in here.

The VGA port works fine, which is kinda weird, but there is no doubt that the HDMI issues comes after connecting a linux laptop. Im guessing they share som HW in the TV. The same laptop with windows has worked fine (as said I have not dared trying Linux again, as I dont want to spend more money on shipping my TV to repairs). As you can see from other posts than mine ( I started the thread), all other people that has bothered answering about their HW specs uses Linux as well. Not necessarily Ubuntu, though.

---

### Post by DjRedo on 2010-05-27
> **Jakiejake said:**
> I don't think that's right
Just Sayin...
Just because some people don't like Linux... :confused:

Im not sure where you're getting with this? I love Linux, if someone gets the impression otherwise.

And the problem might very well be in the TV. It doesnt make it less of an issue. From the reseach I have done, it seems clear that the problem is triggered by connecting a Linux PC.

---

### Post by ronnielsen1 on 2010-05-27
Here's one from Vista

Here's one for Vista
[http://www.techsupportforum.com/hardware-support/video-card-support/393168-windows-vista-red-tint-problem.html](http://www.techsupportforum.com/hardware-support/video-card-support/393168-windows-vista-red-tint-problem.html)

> Im running my Acer Aspire m1021 on windows vista home premium. The odd thing is that the colors r perfect when i switch to HDMI mode, but i just cant get rid of the red tint on my screen when i switch my LCD tv to PC mode. I really dont know what is causing this problem! I tried restoring my computer, but had no luck at all. I tried running oblivion on my PC and even the main menu colors have a red tint to it. everything that is displayed on my tv while on pc mode has a redish tint to it!

I've seen posts claiming it ruins hard drives too and makes you use massive amounts of cdr's

---

### Post by DjRedo on 2010-05-27
> **ronnielsen1 said:**
> Here's one from Vista

Here's one for Vista
[http://www.techsupportforum.com/hardware-support/video-card-support/393168-windows-vista-red-tint-problem.html](http://www.techsupportforum.com/hardware-support/video-card-support/393168-windows-vista-red-tint-problem.html)

I've seen posts claiming it ruins hard drives too and makes you use massive amounts of cdr's

Well, if you want to argue that its not related to Linux, then fine by me. 
It most definitely is in my case. I used the laptop with XP for a while: no problem. I switch to Linux: boom it has a tint when switching to HDMI afterwards. I replace the TV, same story again.

The problem you posted is not all the same either, since VGA works fine on the Samsung TVs that has answered to my post, while the HDMI ports takes a hit immediately when connecting a Linux PC on the VGA port. Im my humble opinion pointing out that there are similar problems with windows is not very helpful, we dont even know for sure that he has not connected Linux to it. 

My point is that that alot of people has identified connecting a Linux PC as being the trigger, then the Linux developers should have interest in finding the source of the problem, even if it is not on the Linux side. If not for anything else, then to let people know what they should check out before buying TVs to avoid being locked out of using Linux as I have been.

Its so symptomatic for forums like this that instead of localizing the problem, people start denying the problem as a fact. My personal belief is that its the TV HW that is bugged, but its still a setback for Linux if this is allowed to continue and Linux is identified as something to avoid.

---

### Post by phr33k-dc on 2010-05-27
Your the man DjRedo!

---

### Post by Ranko Kohime on 2010-05-27
Software can trigger hardware failures that were imminent, but it cannot cause hardware failures exclusive of existing hardware issues.  I know most in this thread will know that, but I'm surprised every day by the people who think otherwise.

To me, this sounds like a serious hardware issue for Samsung.  Unless I hear about this issue getting resolved, I believe I will be staying away from their products for the time being.  (I don't have use of HDTV's anyway except when connected to PC's)

---

### Post by gradinaruvasile on 2010-05-27
Well you should post the hardware specs (output of lspci in a terminal) of your laptop.
Also the driver version that is used for the video card and the exact tv model.

Maybe that would be more helpful than saying Linux or Windows or whatever did this.

Linux doesnt do anything to TVs or whatever - maybe certain video drivers/cards combination do and it would be helpful if you create a bug report al launchpad if it concerns the drivers shipped with Ubuntu.

---

### Post by dustinmarlowe56 on 2010-05-27
i wouldn't be surprised if its not so much the fault of a linux OS as it is just relatively young hardware components on both ends of the connection (tv and pc) i'm thinking that hdmi just needs a little more time to evolve since i have heard of a lot of people having problems with it working correctly and consistently with video game consoles and the like. instability just means that the technology needs to grow and mature some in my eyes.

---

### Post by Sub101 on 2010-05-27
> **dustinmarlowe56 said:**
> i wouldn't be surprised if its not so much the fault of a linux OS as it is just relatively young hardware components on both ends of the connection (tv and pc) i'm thinking that hdmi just needs a little more time to evolve since i have heard of a lot of people having problems with it working correctly and consistently with video game consoles and the like. instability just means that the technology needs to grow and mature some in my eyes.

Couldnt agree more. My house got hit by lightning, the only things that fried were all the HD ports (HD on 2 tvs, HD on set-top box, HD on PS3). All other connections were fine.

---

### Post by DjRedo on 2010-05-27
> **gradinaruvasile said:**
> Well you should post the hardware specs (output of lspci in a terminal) of your laptop.
Also the driver version that is used for the video card and the exact tv model.

Maybe that would be more helpful than saying Linux or Windows or whatever did this.

Linux doesnt do anything to TVs or whatever - maybe certain video drivers/cards combination do and it would be helpful if you create a bug report al launchpad if it concerns the drivers shipped with Ubuntu.

Thanx for posting.

I thought the specs were in the thread i linked for reference, but sure:

The TV is a Samsung  LE40B535

Im not an advanced Linux user, so if you want me to post output from terminal, Id need a helping hand. (ill look into it laters today, right now i dont have the time)

I use a Toshiba Equium laptop, A100-299, with a T2250 Intel Core Duo Processor. The graphics are an Intel 945GM Express onboard card with (up to) 128 MB 							DDR2 RAM (UMA). 

Imrunning Ubuntu 9.10 on a 2.6.31-19 Kernel. I do not know anything more about my graphics driver in Linux, other than I have have kept it upgraded through Ubuntu. Other users claim the problem started after an update to the Linux graphics driver (see reference thread).

---

### Post by DjRedo on 2010-05-27
> **Ranko Kohime said:**
> Software can trigger hardware failures that were imminent, but it cannot cause hardware failures exclusive of existing hardware issues.  I know most in this thread will know that, but I'm surprised every day by the people who think otherwise.

To me, this sounds like a serious hardware issue for Samsung.  Unless I hear about this issue getting resolved, I believe I will be staying away from their products for the time being.  (I don't have use of HDTV's anyway except when connected to PC's)

I would definitely advice people to stay away from Samsung TVs for now, yes. Ive seen the same for other TVs, but Samsung seems to be heavily influated.

---

### Post by Jakiejake on 2010-05-28
> **DjRedo said:**
> Im not sure where you're getting with this? I love Linux, if someone gets the impression otherwise.

And the problem might very well be in the TV. It doesnt make it less of an issue. From the reseach I have done, it seems clear that the problem is triggered by connecting a Linux PC.

Oh I thought you were just trying to turn people off Linux

---

### Post by andytiedye on 2011-05-02
Toshiba QOSMIO X505-Q896.   NVIDIA GTX430M graphics,  1920x1080 display.
Ubuntu 10.10

Tried on 2 Samsung TVs.   No damage to TVs, but no video output either.
Works fine when I reboot into Windows 7.

---

