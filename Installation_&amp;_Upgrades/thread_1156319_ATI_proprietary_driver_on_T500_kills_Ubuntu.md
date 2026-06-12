---
title: "ATI proprietary driver on T500 kills Ubuntu?"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2009-05-11
I have installed Ubuntu 9.04 on my brand new Lenovo Thinkpad T500. Then I was offered to install the proprietary driver for the graphics card, which I did.
From then on, Ubuntu does not boot any more. It shows some garbage on my screen and locks up so I have to do a hard power off.

This is quite frustrating - does that mean the proprietary driver (which seems to be necessary to use the full 3D performance) does not work?
Why does Ubuntu offer to install it when it really kills the system?

How can I correct this problem? As Ubuntu does not even boot any more, I do not know how to remove that driver and reestablish the original state after install. And how can I get full 3D performance when the proprietary driver does not work?

EDIT: with some effort I managed to get rid of the proprietary driver, but even the standard one seems to be crap: when I try to play a video file, the whole X session crashes and I see the login prompt.

It seems Ubuntu 9.04 is not usable at all for me at the moment :(

I probably have to switch to some other distribution or an older version of Ubuntu. 
Very disappointing.

---

### Post by sepimour on 2009-05-21
Hi,

 I am running a T500 and was having some issues with my drivers as well.
I am not completely sure what your setup is / was but I was getting an issue where there would be a 1 second delay if I try to maximize/minimize my windows. 

I am currently running the default FGLRX driver provided by System -> Administration -> Hardware Drivers 
 and all I needed to do to fix my issue was to install this bug fix: [https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

Now everything runs 100%.  I even installed Sacred 2 to test my 3D acceleration and could run the game full graphics.

---

### Post by johann_p on 2009-05-25
So far I am extremely disappointed by Jaunty. Audio does not work right, and the issues with graphics are terrible. No matter if I use the Intel or the ATI chip of my T500, I cannot even watch a simple Flash movie without hangs, stuttering, wrong sync etc.

There seem to be huge problems with Intel graphics drivers and there seem to be huge problems with ATI support. The forums are full with complex, sometimes contradicting reports and howtos and nothing I tried so far could make my experience with the T500 and Jaunty just acceptable, let alone pleasing.

I had been using Ubuntu on several computers previously and I have not experienced such terrible problems with graphics so far. However, audio practically never worked right and as expected on any of the computers.

All these issues are non-existent on these machines under Windows where I have a dual boot configuration. 
I have been using *NIX and Linux for years, but I understand if people give up when the frustration gets too high and hours and hours are spent to get even the most basic functionality to work, like being able to watch a flash movie, use skype or record some audio from line-in. 

My conclusion will be again to give up and just accept that I cannot do some of the things I would like to do on my computer :( :(

---

