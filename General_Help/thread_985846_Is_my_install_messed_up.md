---
title: "Is my install messed up?"
date: 2008-11-18
forum: General Help
---

### Post by 3dmaker on 2008-11-18
Hello all, I have been using Ubuntu since way back in the 6 version. 8.04 was great. Everything worked out of the box, the Repos were good, and now with my fresh install of 8.10 it sucks.First of all it entirely stopped seeing my Broadcom wireless chipset, and I have yet to figure that out, I am currently reading another post I have made, so hopefully I will get some progress with that. I have also enabled all open source repos in Synaptics, and why can't it find VLC? VLC is so essential to anyone who knows anything about video. Why isnt it there? What is going on with this installation?

---

### Post by amp_man on 2008-11-18
> **3dmaker said:**
> Hello all, I have been using Ubuntu since way back in the 6 version. 8.04 was great. Everything worked out of the box, the Repos were good, and now with my fresh install of 8.10 it sucks.First of all it entirely stopped seeing my Broadcom wireless chipset, and I have yet to figure that out,

You probably need to blacklist the new b43 driver, if you're using ndiswrapper. Otherwise, you need to give b43 some firmware.

> I am currently reading another post I have made, so hopefully I will get some progress with that. I have also enabled all open source repos in Synaptics, and why can't it find VLC? VLC is so essential to anyone who knows anything about video. Why isnt it there? What is going on with this installation?

It should be in the multiverse repo, you sure you have that enabled?

---

### Post by easoukenka on 2008-11-18
you can download VLC right from there website and saying anyone who knows anything about video use vlc kinda rude I prefer mplayer   

Check your sources.list file for what repositories are on most likely there was a conflict of some sort and its simply just #commented out

goto medibuntu add that repository is a good idea also

As for wireless well linux is always struggling with wireless what fixed other peoples problems has messed yours up just google linux driver and your chipset should take about 30 minutes

A few troubleshooters for you 

go into terminal do ifconfig find what your card is labeled like ath0 then do sudo ifconfig ath0 down then sudo ifconfig up run dmesg see what happened take a look at iwconfig options.

Load up your old working bootable linux distro check what settings worked good luck

---

