---
title: "Complex multimonitor under Ubuntu"
date: 2013-12-07
forum: Hardware
---

### Post by bbasbagill on 2013-12-07
**_Introduction:_**
Most people are happy with a laptop/tablet or traditional desktop with 1 keyboard, 1 monitor, 1 mouse...  but for some people this is not enough.  As a poweruser leaves the mainstream traditional workflow and places higher demands on their interface, it becomes more and more difficult to build, maintain, and find support for a machine that meets their needs.  I have been working with multimonitor configurations over the past few decades on various platforms from OS/2, Windows, OSX, to Linux.  Each scenerio presents its own unique challenge (and I use the word "challenge" lightly), I dont blame the companies behind the technology involved for being reluctant to spend money and resources to support such overly-customized configurations.  Users on the bleeding edge of technology must rely on their own wits and the advice of others in order to accomplish their goals.

Multimonitor is an area that Ubuntu and Linux in general seems to be particularly weak at when compared to OSX and Windows.  This is a shame because "back in the day" this is the sort of thing Linux rather shined at.  X was extremely flexible with multiple workspaces when compared to the other platforms.  It still is but we have built so many layers upon layers on top of X that now, with the recent popularity of compositing extensions and tren of the major window managers to require it, the old Xinerama approach has become useless and we all have to step back to "re-invent the wheel".

I hope the forum doesnt mind if I take a few minutes to dump some things out of my head for future reference, to invite advice of others in simliar situations, to help others tha may be struggling with similar issues, and hopefully to spark some much needed progress in this area.  I've tried to temper a rant with logical analysis and a plea for help.


[B]_Ubuntu is limited to 1 desktop per GPU_:
[/B]Wether it's nvidia, ati, or intel.. wether it's opensource or propietary drivers.. if you want to max out the number of displays on your machine the first limitation you are bound to encounter is that you can have whatever number of displays you can attach to a single GPU.  Don't expect to be able to drag windows from one display to another or span anything accross multiple monitors unless they are all on the same GPU.  I have used single or multiple multi-gpu cards.. and multiple single GPU cards using sli and crossfire bridges in various configurations but after digging through the internet and experimenting.. one big hurdle I have not been able to overcome is that a single X desktop is bound to a single GPU if want to use a modern desktop and not resort to an unsupported old fork that only works half the time when you're lucky.

In windows and osx, I can drag windows and span full screen video accross multiple GPUs and mutiple cards.  I can drag windows from any monitor to any other monitor and it works.  Sure there may be some video tearing or window snapping when they jump GPUs, it's not perfect and it's not seamless but its functional.  Linux cannot drag windows from one gpu to another without Xinerama.
**_Xinerama is dead_:**
Time and time again, whenever I research problems for multimonitor under linux, one of the first solutions I reach is to enable Xinerama.  Once upon a time, in a galaxy far far away, Xinarama was a convenient way to tie X desktops together and act as one "Big Desktop".  This worked for years and was great until we started adding layers of UI on top of X.  There's one problem, Xinerama is not compatible with compositing extensions and cannot be used with any modern desktop.  Sure you can go to an older desktop environment or a "fallback" mode..  but good luck with that, how long can you find that acceptable before all the cool cool kids are doing things no longer supported by your obscure fork?  If you come accross a random forum post asking you to add *Option "Xinerama" "on"* to your xorg.conf you are pretty much wasting your time.  OMG please correct me if I'm wrong I have wasted days if not weeks or months of my life exploring this. 

**Twinview**** is a Hack:** Twinview is a propietary implementation by nvidia of Xinerama integrated into their propietary drivers.  This is a huge leap forward for dual-head cards, thank you nvidia for at least trying. I've had multi-head nvidia cards but have found no way to implement twinview accross multi-GPU even on the same card.  This is a convenient hack but realistically only gets you up to 2 monitors per X desktop.  A user on [HTML]http://ubuntuforums.org/showthread.php?t=1999966[/HTML] describes getting multihead twinview to work but i have had no success with any cards I've tried, maybe you need to buy their expensive quadro line but I've ditched that option and instead went with ATI Eyefinity.  Please reply if you have had more success using nvidia with this approach as I've been banging by head against the wall with this for hours of lost sleep accross years trying to explore it.  Even if I did dump my checkbook into nvidia quadro I dont see it getting me past 1 card (which is significantly more $$$ for fewer displays than eyefinity) per desktop.

**_Eyefinity6 is the best you can hope for_**[B]_ under a single X desktop_:
[/B]So, there is an obscure version of Radeon HD called "Eyefinity 6"... maybe you've heard of it?  Forget stringing a few mainstream ati or nvidia cards together for multimonitor that's pretty much a dead end with the current state of Linux.  (does intel even have a serious approach to multimonitor? are there any other players?) However, ATI makes a special breed of video cards called "Eyefinity" which provide you with more video outputs per GPU than quadro or anything else on the mass market for a reasonable price as far as I can tell.  Within the Eyefinity line are the "Eyefinity 6" cards which are as far down the rabbit hole as I can find... 6 accelerated displays with multiGB vram on a single gpu and supported by their propietary drivers under Linux.  Sure, you gotta spend some $$ for miniDP to DVI active adapters or whatever but it gets the job done.  This takes you up to 6 displays per X desktop. I've done a 2x3 or 1x5 (there are bulk resolution restrictions that come into play) panel displays and have been happy under all desktop environments with regard to gaming, video, and application performance for several years now.  Much more flexible than anything I've explored under nvidia or intel.

Unfortunatley, even with dual crossfireX links, I have been unable to get past the 1 desktop per gpu restriction. I have been able to to do dual 2x3, that's 12 displays on 2 desktops under Unity, Gnome3, and KDE4 with full accelerated video and dragging windows accross displays on the same X desktop... using multiple eyefinity6 cards.  There are significant hurdles to overcome such as per-application bugs per workspace but overall it is functional.  There has been some discussion about GPU object support being developed for X so all GPUs can be handled under the same desktop like OSX and Windows but its been years since I've been able to find any significant progress in that direction.
[B]

_Desktop environments ignore multiple X sessions_[/B][B]:
[/B]The only environment that "out of the box" supports multiple X desktops... in other words, after you get the whole xorg.conf nailed down and get multiple X desktops accross your displays, you actually get a laucher or taskbar or whatever to start using applications on your secondary dsiplay... is KDE.  Under gnome you have to manually start a secondary shell with "gnome-shell -replace --display :0.1" or unity with "compiz --replace --display :0.1" added to your startup before you can use your secondary displays.  This is a clear indication that the main development for each of these project have little concern for mulimonitor.


It has been difficult to get as far as I have.  I currently have a 2x3 panel array + 1 projector on my main workstation for a total of 7 displays using 2 desktops under gnome.  This would have been under an hour of configuration with Windows or OSX but has been over a year to figure out under Ubuntu.  I welcome any input and discussion on how to better handle complex mulitmonitor configurations under Ubuntu.

---

### Post by houkouonchi2 on 2014-02-02
I just stuck to XGL for compositing with multi GPU although I am pretty sure I got non-compositing working as well with multi nvidia GPU's but I just couldn't do desktop compositing on this setup unless I used XGL.

Anyway i just thought I would mention that modern nvidia cards can now output 4 displays with twinview and with disalbing xinerama info sent on twinview it can be used as one big desktop

---

### Post by elseco on 2014-04-14
I have had the exact same issue for years. I am looking forward to the day when linux supports multi-gpu's with compiz. Meanwhile, I also went with Eyefinity. It is basically my only option.

---

### Post by bcschmerker on 2014-08-03
Thanks for spotlighting problems with multiple displays on Ubuntu®.  As of 3 August 2014, work on tuning an eMachines®/Acer® EL1210-09 upgraded with a Shuttle® PC6300001 power supply for projection duty has stalled; in my case, AMD® Eyefinity&#8482; is *not an option* due to the planar chipset.  Acer Computer used the nVIDIA® nForce® 785 chipset (with an integrated 64-bit GeForce® GPU that I am unable to disable from BIOS Settings) in the EL1210-09, and nVIDIA Corporation and Advanced Micro Devices have a long history of GPU hardware conflicts going back to ATi Technologies as an independent company. 

I plan to use either the PNY® NVS 285 (nVIDIA® GT218 GPU, 512 MB DDR2) or PNY® NVS 315 (nVIDIA® GF119 GPU, 1 GB DDR3) running X.org Nouveau; I have awaited performance reports for both cards for months, with no results.  Earlier tests with three different package groups of nVIDIA® Drivers on two different consumer half-heights built on the nVIDIA® GT218 GPU have failed; no-login-screen conditions resulted, contraindicating the drivers for projection duty.

**Update:**  Due to instability in both the development Kernels and the drivers for the nVIDIA® GF119 as of March 2015, I have been forced to restart, at the first available opportunity, the projection-computer project around an Asus® CM1630-06 with select upgrades, as the ATi® RV970 Pro is supported by a far more stable set of X.org drivers than are the nVIDIA® C77, GT218, and GF119 for the EL1210 project.

---

### Post by OneOldFish on 2014-08-25
you just made me want to shot my self :( i used Ubuntu since 6.10 and was a huge fan up until unity came in . i have been using a 4 screen system and just cant understand how they can decide that muiti monitor is not the future. i mean its like taking a car and instaling a 25hp engine in it with a 3 speed trany and painting it realy shiny and saying now that way better then what we had before WTF. i was about to come back to ubuntu and try to figure out my 4 screen conf. but you just destroyed me with this post. i kind of know this would be the outcome but dead right out of the box. thanks for the info. you just saved me a ton of time and effort on something that was never going to happen. :) back to WinBlows but at least they have what i need. buy the way do you have any idea why Fedora seams to be able of handling 4 screens out of the box?

---

### Post by mickaelperrin on 2014-10-08
Hi,

If only I saw your post some weeks ago, it would have save me some days full of frustration trying to succeed in my multinomitor setup.

Thank you so much for your informations regarding the ATI Eyefinity 6, I am currently trying to find one refurbished and I will install it in my eGPU setup for my Lenovo X220.

Some details however, I think the situation is maybe better for multiGPU. Indeed, it seems that with the release of RandR 1.4 some people are reporting that multiGPU works.

However, it didn't work for me. I think essentially due to the use of two video cards of two different manufacturers (The binary Nvidia drivers seems to overwrite the default ones).

I will give you some feedback if my install with an Eyefinity 6 worked as expected.

Regards,

Mickaël

---

