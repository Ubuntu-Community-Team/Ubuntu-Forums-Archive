---
title: "Is it possible to run 4K video?"
date: 2016-06-25
forum: Hardware
---

### Post by milagre23 on 2016-06-25
Hi,

I have been using OSX since 2008 for video editing and some music production (but always using Linux in my laptops). Now I have decided, since my iMac is dieing, to try a FOOS approach, and so, I'm in the process of setting up a PC and install Ubuntu Studio (witch I have used in the past) and work with open source software (I'm particularly interested in Blender). At the moment, my biggest concern is screen compatibility issues. I have searched quite a bit in the Internet, and in this forum, and is really difficult to know if some resolutions are or nor possible to setup in Linux, in Ubuntu family, specially in Ubuntu Studio, since most part of the time the information is not clear and sometimes is contradictory. 
I'm referring to 21:9 (2560X1080) or 4K (3840X2160).

So my questions are: 

Is it possible? Does anyone have tried with success? And how?

Many thanks in advance and best regards from Portugal.
J

---

### Post by gordintoronto on 2016-06-26
What is your video card? Monitor?

---

### Post by milagre23 on 2016-06-27
> **gordintoronto said:**
> What is your video card? Monitor?

I'am still assembling the PC.  I was thinking in a PNY NVIDIA Quadro K620 2GB DDR3.
The monitors, I have to choose between LG 34' 34UM67-P UltraWide 21:9 IPS or Asus 28' PB287Q 1ms UHD 4K.
What do you think?

Many thanks for your interest

---

### Post by CrocoDuck on 2016-06-27
Of course it is possible! It just depends on the Video Card you want to use, which resolutions it supports and if there is at least a driver for Linux that supports it (with all the needed functionality). I never had troubles not even with multiple monitor setups. I usually avoid dedicated video card as my focus is audio, so I am not an expert. I am just fine with Intel integrated stuff and I only used old ATI's and NVIDIA's. ATI and NVIDIA should have plenty of supported models. I think that the best source of info is the Arch Linux wiki. It is plenty of info and should point you to the right direction at least to know whether a card is supported and by what driver (yes, there are many drivers under Linux). Beware that although the same drivers should be available on Ubuntu Repositories (and configurable with probably the same sort of instructions) the version (and hence the functionality) might be different. Make sure you have enough support before you buy.

[NVIDIA (Arch Linux Wiki)]("https://wiki.archlinux.org/index.php/NVIDIA")
[ATI (Arch Linux Wiki)]("https://wiki.archlinux.org/index.php/ATI")
[URL="https://wiki.archlinux.org/index.php/Intel_graphics"]Intel (Arch Linux Wiki)

[/URL]As a rule of thumb, slightly older video cards are a better deal as drivers should be mature for supporting them. Newest devices might still need the support to be developed for them.

---

### Post by milagre23 on 2016-06-27
Many thanks CrocoDuck. Very useful. I'am going to check the Arch Linux Wiki.

---

### Post by gordintoronto on 2016-06-27
I have no personal experience with quadro video cards, but from what I have seen in the forums, they seem to be more of a problem than a solution. The best performance seems to be last-year's gang-busters gaming card. GTX9xx!

I have had bad experience with LG monitors, and wonderful (corporate) experience with HP IPS monitors. I have a 24-inch monitor on my desktop, and it's large enough that I sometimes lose the mouse cursor.

---

### Post by DuckHook on 2016-06-27
> **milagre23 said:**
> I'am still assembling the PC.  I was thinking in a PNY NVIDIA Quadro K620 2GB DDR3.
The monitors, I have to choose between LG 34' 34UM67-P UltraWide 21:9 IPS or Asus 28' PB287Q 1ms UHD 4K.
What do you think?Firstly, to your larger question:

Ubuntu has come a long way. It is pretty good these days supporting large screen formats provided that you stay with well-known and widely-used components. The really old, really new and really specialized are the three areas that tend to create problems for Linux. Personally, I run a 4K monitor on an AMD HD7950 from a rather obscure OEM and it works splendidly. I should qualify that: it works splendidly for *my* purposes&#8213;which are all about screen real estate and not colour accuracy. If you do video editing and other photo-realistic work where colour accuracy is crucial, then you will find Linux more obscure and difficult to work with than Apple, which is built from the ground up with painless video accuracy as a goal. I don't want to discourage you either, because it is clearly possible: many of today's Hollywood films are created and rendered on Linux software, so of course it's possible&#8213;it's just more difficult&#8213;and this is a consideration you should factor into your decision. For example, there is no colour profile for my monitor anywhere in the Linux-sphere. If I cared about colour accuracy (which I don't), I would have to go through the painstaking calibration steps to build my own. Video card is more critical than monitor because that is where most support issues arise.

Lastly, I am moving your thread to the Hardware forum. The nature of your question is essentially a HW one and you should attract more attention there. I have also taken the liberty of editing your title to add more detail.

---

### Post by CrocoDuck on 2016-06-28
> **DuckHook said:**
> If you do video editing and other photo-realistic work where colour accuracy is crucial, then you will find Linux more obscure and difficult to work with than Apple, which is built from the ground up with painless video accuracy as a goal.

Probably this is true as long as the OS is concerned but, regarding hardware, nowadays Macs use standard Intel cards or NVIDIA cards (on my corporate MacBook Air I have an Intel HD Graphics 6000 1536 MB). It could be maybe profitable to have a look at which cards are inside the macs and check whether they are Linux compatible (most should be)... Given what DuckHook said about the rest I bet it wouldn't get you much closer to emulate actual Mac color performances tho...

> **DuckHook said:**
> many of today's Hollywood films are created and rendered on Linux software, so of course it's possible

Yeah, an impressive number of Hollywood movies were rendered on Linux. However, I am not sure whether the Linux machines were High Performance Clusters devoted to render tasks only or also the modelling and editing took place on Linux. It could be either case really. Kinda off topic, but do you have any more detailed info?

By the way, nice name! Nice to see another Duck dude on the web!

---

### Post by Linuxisfast on 2016-06-28
I run two 4K monitors with my nvidia 960GT with no issues.

---

### Post by milagre23 on 2016-06-28
Thanks gorditoronto.

---

### Post by milagre23 on 2016-06-28
Thanks DuckHook, for the advise.

> **DuckHook said:**
> 
Lastly, I am moving your thread to the Hardware forum. The nature of your question is essentially a HW one and you should attract more attention there. I have also taken the liberty of editing your title to add more detail.

Yes, you are right. Thanks again.

---

### Post by milagre23 on 2016-06-28
> **Linuxisfast said:**
> I run two 4K monitors with my nvidia 960GT with no issues.

Good to know! 
Thanks.

---

### Post by Liam_Murphy on 2016-06-28
Should be out of the box pretty much. 

As long as you have the proper multimedia packages, which you can allow Ubuntu to download when you install it, and you have a GPU that can handle it, all good. 

You can have a guaranteed good experience with open source drivers. 

I remember having fullscreen issues with the proprietary AMD drivers, I hear NVIDIA is fine.

---

### Post by DuckHook on 2016-06-28
> **CrocoDuck said:**
> ...do you have any more detailed info?The best I could find was [this]("https://en.wikibooks.org/wiki/Movie_Making_Manual/Linux_in_film_production").

> Nice to see another Duck dude on the web!*chuckle*

My "Duck' reference refers to the sad shape of my typical ball flight. Believe me, it's one Duck I'm not proud of. #-o

---

### Post by dean.w.schulze on 2016-08-13
I can't run one 4k monitor at UHD resolution on my GeForce gtx 960.  There must be an important difference between your 960gt and my GTX 960.

---

