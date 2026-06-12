---
title: "nVidia vs AMD"
date: 2014-10-10
forum: Hardware
---

### Post by pieroxy on 2014-10-10
Hello all,

I've been rebooting every 15 minutes for the last week since I updated my computer and the latest open source AMD driver got installed, unstable as hell. Long story short: I can't use my computer anymore.

My chipset being too old to install the proprietary drivers, I'm kind of stuck. So my options are:

1. Roll back the latest packages. Seeing how smooth an upgrade (from one release to another, not regular updates) is, I'm not even going to try that one by fear of destroying my distro.
2. Reinstall everything with 12.04
3. Spit 25&#8364; to buy a new GC

I'll go with 3. My question is: which chipset? I've traditionally been an ATI guy so I'm used to crappy drivers. The only time I tried a fanless NVidia card it burned after a few month of usage...

Here are my usage scenario:
1. No 3D / Gaming
2. No fan. I want a quiet one
3. Best 2D acceleration possible given the first two parameters.

So I call for help to the combined experience Ubuntu community over which chipset I should buy. My options (that I can see) are:

GeForce 210, GT610, GT720, GT730, 
RADEON HD5450, HD4650, HD6450, R5 230, R7 240, R7 250

So please tell me your experience.

---

### Post by oldfred on 2014-10-10
I have always been an nVidia user. EVen though my 7600GT exploded. Actually capacitors made loud pop and system died.

And the open source drivers for nVidia have rarely worked for me. But once I install the proprietary nVidia driver system has always run well. And while they eventually freeze an older driver, it still is available for those older cards and may get minor updates. I actually think that helps the newer driver not have too much code for very old cards and not have code that old card could not use.

It seems AMD is changing Linux drivers around again.
 The Slides Announcing The New "AMDGPU" Kernel Driver
[http://www.phoronix.com/scan.php?page=news_item&px=MTgwODA](http://www.phoronix.com/scan.php?page=news_item&px=MTgwODA)

---

### Post by gifford on 2014-10-10
I can appreciate your dilemma. Had a similar situation when upgrading my laptop and my wife's to Ubuntu 14.04. Although the computers were about the same age, hers having a Nvidia chip and mine ATI/AMD, there was
no proprietary driver for mine but Nvidia still supported hers.
I recently replaced my burnt out ATI/AMD card in my workstations with a Nvidia Quadro 4000 and now am glad I did. I too had always used the ATI/AMD cards as I assumed they were more Ubuntu Linux friendly with drivers
and support. I do not believe that is the case anymore and will not shy away from using Nvidia as my experience has so far been very positive. 
As I can not answer your question about the specific cards you have listed, I can tell you in my recent experience with Nvidia everything has worked as expected and I have no hesitation in recommending using their products with Ubuntu.

---

### Post by Michael_McKenney on 2014-10-10
The problem is neither Nvidia or AMD/ATI will make optimized drivers for Linux.  No money in it for development.

---

### Post by Kim Foltz on 2014-10-10
I have used the HD5450 with Kubuntu 14.04 and both the Xorg and fglrx-updates drivers work well with the card. It sells for roughly $10 after rebate on NewEgg so it is cheap to experiment with. The only problem is suspend and resume doesn't work well on my computer but I doubt it is a problem with the video card.

---

### Post by MartyBuntu on 2014-10-10
Go NVIDIA for fewer headaches.

---

### Post by Mark Phelps on 2014-10-11
AMD makes restricted drivers for their HD 5x-series, HD 6x-series, and for their R5 and R7 series.  The HD 4x-series are now "legacy" drivers (no longer in development), and many folks report having problems with the newer R9 series.

---

### Post by pieroxy on 2014-10-13
Thanks for your input. I just bought a GeForce 210. Will report back when it arrives in the mail.

---

### Post by sp40140 on 2014-10-13
I run GeForce 210. Works great. No issues. I have HDMI port hooked to my 60" LG. Open source drivers on Ubuntu 14.04.01

---

### Post by pieroxy on 2014-10-20
I got it. I even installed proprietary drivers which gives me better performances. Almost all is well.

I have dual screens and the VGA one doesn't get to sleep anymore when the energy saving settings kicks in... Any idea?

---

