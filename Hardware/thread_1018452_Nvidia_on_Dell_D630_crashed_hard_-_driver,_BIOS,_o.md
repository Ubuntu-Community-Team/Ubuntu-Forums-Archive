---
title: "Nvidia on Dell D630 crashed hard - driver, BIOS, or hardware the culprit?"
date: 2008-12-22
forum: Hardware
---

### Post by AllisonM on 2008-12-22
I'm sorry if I've missed a solution to this problem - I have been looking for a few days, but I'm new here. I have a potentially serious graphics card problem that I could use some advice on. Sorry for the epic length. 

I used to have a dual boot Windows XP/Edgy laptop, but after buying a new laptop I abandoned Ubuntu for awhile. (I say this so that you can know that I was never a pro, and I'm a bit out of date, but I'm not completely unfamiliar with this stuff.) This Christmas I have a bit of free time, so I've been drifting back. I started by installing Wubi and Hardy Heron on my Dell Latitude D630,  which runs Vista. 

My graphics card is an Nvidia Quadro NVS 135M. I installed the Nvidia drivers available in driver manager. Specifically, I installed 177, but I found that it pulsed my fan strangely, so I switched to... 173? (These numbers are out of my head, hope they're right.) That one seemed to run fine.

That evening, I was booted into Linux, watching a DVD on my external monitor while my laptop charged - so probably running a bit hot - when the computer locked up. The screen froze, the mouse froze, even the indicator lights froze. When the computer booted up, I had two grainy, low-res displays on my laptop screen, one stacked on top of the other. 

Vista ran startup repair a couple times, then made quite a few changes through chkdsk (unfortunately, I didn't take notes) and finally booted with normal display. Stupidly, I took this to be a problem with Ubuntu, and uninstalled Wubi. Even once my display looked normal, I wasn't able to play DVDs in Vista - nothing happened when I told VLC to open disc. 

The next morning, everything, including DVD playback, was fine. But that night, while I was again watching a DVD and charging my laptop, this time in Vista, exactly the same thing happened. 

So, I figure, this is a hardware problem. I now know there are big problems with my Nvidia card, so I figure it's failing and call Dell tech support. They encouraged me to update my driver and BIOS, and then try to provoke the same error. If it still crashes, they say they'll send a tech to replace my graphics card.

BUT now everything is running just fine - I  ran a DVD for two hours, four times as long as last time, while my laptop charged, and it didn't even stutter. So here are the possibilities, as I see them.

1. The card is failing, but its failure has been slightly delayed by the new BIOS and driver, which run the fan more. It is entirely coincidental that it started to fail right after I installed Ubuntu. I should replace the card and reinstall Hardy Heron with the 173 driver.

2. The card is failing because, for a day or so, I ran an outdated Nvidia driver that didn't run the fan enough. Because my card has high failure rates, this slightly higher-than-normal temperature wrecked it. If this is the case, I need a new card, but I also need to be careful in my configuration of Ubuntu. If this is the case, I need to figure out a way to run the 177 driver without going insane - maybe I need a utility to take over and slow down the fan, but not so much that my computer overheats. 

3. My outdated BIOS (it was version 3, now it's version 15) was the problem. This is why I had the same error in both operating systems. My card is still delicate, but not permanently damaged, and it should run fine under the new BIOS on both systems, though my battery life has taken a hit.  

I welcome any (1) guesses as to which of the three scenarios I'm in, (2) alternative scenarios, (3) suggestions on how to proceed.

---

### Post by AllisonM on 2008-12-22
This morning my Nvidia card died completely - I can't boot at all, and Dell has agreed to replace it. Is there any chance that Ubuntu caused the failure? Should I hold off installing Hardy Heron once it's fixed? It seems like too much of a coincidence that my card, which had run perfectly, failed within 12 hours of activating accelerated graphics in Hardy Heron.

---

### Post by AllisonM on 2008-12-26
Bump? Should this be in the Dell forum?

---

### Post by jegreat on 2009-10-25
hey m facing the same problem. m having Ubuntu 9.04; installed ubuntu but i have updated the system. and its crashing my graphics card and it keeps on bringing nvidia errors etc.

i bilieve its the ubuntu updates coz when i choose the former kernel from my kernel lists during boot, i works fine, but when i choose the new kernel (the one i updated to) i get card errors!!

---

### Post by jegreat on 2009-10-25
hey m facing the same problem. m having Ubuntu 9.04; installed ubuntu but i have updated the system. and its crashing my graphics card and it keeps on bringing nvidia errors etc.

i bilieve its the ubuntu updates coz when i choose the former kernel from my kernel lists during boot, i works fine, but when i choose the new kernel (the one i updated to) i get card errors!!

---

### Post by jegreat on 2009-10-25
indeed the screen keeps hanging, freezing, bringing strange images, it gets stack etc. m running crazy realy. i wonder wats going on here!!

---

### Post by bpickel on 2009-11-05
Actually, the problem described in the first post is hardware related. I am an IT manager with around 400 Dells in my fleet.   NVIDIA had a flaw in the 95nm manufacturing process that caused many of the aforementioned cards to fail in the way described. This is brought on by heat.  Dell has released a BIOS fix for this. It you have not upgraded your D630 to the A16 or greater BIOS, doing so will save you some inevitable grief. I have personally witnessed in excess of 20 machines succumb to this issue. If you have already been bitten, Dell will replace your card. :mad:

---

### Post by recluce on 2009-11-06
> **bpickel said:**
> Actually, the problem described in the first post is hardware related. I am an IT manager with around 400 Dells in my fleet.   NVIDIA had a flaw in the 95nm manufacturing process that caused many of the aforementioned cards to fail in the way described. This is brought on by heat.  Dell has released a BIOS fix for this. It you have not upgraded your D630 to the A16 or greater BIOS, doing so will save you some inevitable grief. I have personally witnessed in excess of 20 machines succumb to this issue. If you have already been bitten, Dell will replace your card. :mad:

Unfortunately, bpickel is completely right. Only about a dozen afflicted Latitudes in my company, but 3 have already failed and were repaired by Dell.

The failure the OP described is fairly typical: some freezes or display errors first, then, after a various amount of time, the machine dies. That you just updated Ubuntu is completely incidental to this. 

The only variables influencing the death of the GPU: what BIOS version (with increased fan activity or not) and how many hours the GPU spent at higher temperatures (GPU-intensive games vs. idling at the desktop, for example).

Also: the D620 and D630 seem to be running hotter than their 15" counterparts D820 and D830 - probably because of the smaller form factor.

So what to do? Get the laptop repaired, make sure you have A16 BIOS on it and proceed as if nothing had happened. :roll:

---

### Post by Alcoatari on 2009-12-09
> **bpickel said:**
> Actually, the problem described in the first post is hardware related. I am an IT manager with around 400 Dells in my fleet.   NVIDIA had a flaw in the 95nm manufacturing process that caused many of the aforementioned cards to fail in the way described. This is brought on by heat.  Dell has released a BIOS fix for this. It you have not upgraded your D630 to the A16 or greater BIOS, doing so will save you some inevitable grief. I have personally witnessed in excess of 20 machines succumb to this issue. If you have already been bitten, Dell will replace your card. :mad:


When you say "dell will replace your card," was this a recall issue, or they will replace it only under warranty?

I just bought a used d630 and I thought the issues were screen related, but after upgrading the bios and video drivers, as well as the chip-set drivers, it still has some minor issues. Once out of every 5ish uses, the video will fail, and lock everything up. Then I have to do a hard reboot.

My d630, supposedly has another 400 days left on the warranty, but I have upgraded the chip from 1.8 to 2.4, this was before I knew it had warranty left.

My brother is IT at my company (who uses this same model), so I have a couple of options. I want to know if you guys think I should put everything back the way it was and try to get DELL to fix my problem through the warranty, or try the old switcheroo through my workplace IT?

---

### Post by cosmicbuff on 2010-01-25
indeed looks like hardware flaw, i had similar problem **twice**. second time being now, i run a compaq presario v6106 with nvidia 6150,with AMD turion 64X2

first time it crashed when i was a windows user,2 yrs back,i got the whole motherboard replaced,the company  blamed it on the AMD ,which heats up really mad,an also the Nvidia card adding more insult.

for the last  1 year been a linux user,i didnt do much with this notebook,but watched some movies occasionally and few games. recently my card gave up,though it is being detected well and passes all console commands in flying colours.i can sense its senescence :D

I thought it was an ubuntu problem with the new kernel and driver i installed,i downgraded to 173,then also tried the manual 190 from nvidia.
I also tried three other distros :D,result is the same,so i will leave it in peace..

next time i will avoid AMD,

---

