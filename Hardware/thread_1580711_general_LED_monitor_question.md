---
title: "general LED monitor question"
date: 2010-09-23
forum: Hardware
---

### Post by eotakos on 2010-09-23
Hello everyone,

This thread is not that much related to ubuntu, actually It has nothing to do with it. But where can it be better to post your question other than your favorite forums :-)

So here is the question: Is there a possibility that a latest technology led monitor is somewhat incompatible when used with its analog input?... and I won't go too far, lets stay with the basic stuff... like going into standby when you switch off your pc for instance :-)

Here is the deal: I bought samsung bx2350, and while I am impressed with the colors and everything, while it is supposed to be ultra-eco-friendly, it doesn't go to standby mode; not in the case you have programmed it to sleep after some idle time in a session, not even when you switch off and go to sleep yourself. So I guess all the energy preserved with high tech innovation leds and stuff is wasted by the lack of 20 year old invention: standby  :-)

I just can't believe that I took the faulty monitor out of the stack! because I put aside the one that was on the top, and I chose that one! Can I be that unlucky?! --I'm kidding; I know that I am -when it comes to picking hardware at the stores- but I would like your feedback at this one.--

So please share your ideas, because I'll take a 1hour train (+1 hour back) to change the monitor for one of the same model that -hopefully- goes into standby... and I wouldn't want to make all this effort for nothing (I mean if there is a possibility that something like this is normal for new monitors)

Thank you very much for your time!


ps. I don't know if you can tell by my message, but I haven't bought a monitor in like ten years, and I have no idea of the habits monitors may have these days :-) chears

---

### Post by cascade9 on 2010-09-23
You might have been unlucky. I've got a Samsung BX2240 (LED as well) and it goes into standby just fine. 

When you turn your computer off, do you get the 'check signal cable' msg on the monitor, or does it just stay on with no msg?

---

### Post by eotakos on 2010-09-23
I get the "check the signal cable" sign (this is also supposed to be some kind of self testing for the monitor) but it stays there, wondering around like forever! 

If yours works then I guess mine should as well... I suppose I was unlucky once again

thank you very much for your reply!

---

### Post by cascade9 on 2010-09-23
If you are getting the 'check signal cable'with the computer turned off,a nd the cables still plugged in, I'm guessing that you have got some error. I onyl get it when I have the monitor unplugged from the computer. 

Err...I forgot one thing, I'm using DVI (digital), not VGA (analog). I'll see if I can find the VGA cable that came with this monitor, maybe it will have the same problem with VGA.

> **eotakos said:**
> thank you very much for your reply!

No problem. ;)

---

### Post by eotakos on 2010-09-23
> **cascade9 said:**
> If you are getting the 'check signal cable'with the computer turned off,a nd the cables still plugged in, I'm guessing that you have got some error. I onyl get it when I have the monitor unplugged from the computer. 

that's the thing! it's the most crazy thing to go wrong!

> **cascade9 said:**
> 
Err...I forgot one thing, I'm using DVI (digital), not VGA (analog). I'll see if I can find the VGA cable that came with this monitor, maybe it will have the same problem with VGA. 

hm... yes - I'm using the monitor with my laptop that only has analog output. So that's why I had to ask... is it possible that they took care of everything and they forgot all about the old fashion analog signal?

If you could check what happens with the VGA cable I would be much obliged. I'll be waiting for your answer/ so even if you don't find the cable please post back about it....

thanks again

---

### Post by efflandt on 2010-09-23
Did you ever think that lack of standby might have nothing to do with your monitor, but possibly something to do with your video card/chip or drivers.  What video chip is your system using and what driver (default or proprietary)?

For example my old desktop has legacy ATI X1300 video, and when I installed Lucid, my computer would not go into suspend or hibernate.  The screen would blank, but the video card would not go into standby or shut off.  Other video was also slow.  Apparently my video did not like the new kernel mode setting (kms) drivers.  Once I used **nomodeset** or more card specific **radeon.modeset=0** kernel boot parameter to use the old user space modules instead, video was quicker (like 9.10) and suspend/hibernate worked.

While HDTVs do not usually do DPMS (video card controlled standby), virtually all modern monitors should, especially Samsung.  The last Samsung monitor I had was an HDTV ready 19" 1280x1024 4:3 LCD Monitor, and it would go into standby and wake up fine (whether DVI or VGA).

I am currently using a 32" LG HDTV as a monitor, and it does not do DPMS, so it does not go into standby when the video card tells it to.  But if it gets no signal it goes into a self screen saver mode and shuts off after 10 minutes.  I have to manually wake it up.

---

### Post by eotakos on 2010-09-23
thanks for your reply efflandt,

My laptop's video card is nvidia gs9300M , and I have tried the monitor both with ubuntu -the recommended proprietary driver- and windows with  samsung's driver. But let's forget about the software, because when you turn off the pc it is just hardware; isn't the monitor supposed to go into standby when the cable is connected but no signal gets through? 

I know that I have connected this same laptop with much older lcd monitors and it worked just fine! - if such a thing happened before I'm sure I would have noticed... 

I guess it is normal for TVs to have different standby features.

---

### Post by cascade9 on 2010-09-24
> **eotakos said:**
> But let's forget about the software, because when you turn off the pc it is just hardware; isn't the monitor supposed to go into standby when the cable is connected but no signal gets through? 

Yes, that is what its supposed to do. 

BTW, I checked my monitor with a VGA cable, worked just fine.

---

### Post by eotakos on 2010-09-24
thank you very very much! I didn't have any other way to check this...

you really save me...   (I still have to travel in order to replace it though :-) )

---

### Post by cascade9 on 2010-09-26
Annyoing that you have to travel to get it replaced. :( 

Ohh well.  Better to have a working monitor than one that doesnt go to standby ;)

---

