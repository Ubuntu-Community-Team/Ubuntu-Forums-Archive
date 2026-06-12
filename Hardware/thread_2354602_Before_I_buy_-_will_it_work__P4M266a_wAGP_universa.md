---
title: "Before I buy - will it work?  P4M266a w/AGP universal - Geforce MX440"
date: 2017-03-04
forum: Hardware
---

### Post by michael351 on 2017-03-04
I dug out my old VIA P4M266a mobo w/ Pentium processor to see if I could install Ubuntu 16.04 32 bit.

IT WORKED. Grub was a problem, but I finally have a functioning system from power on.

It is quite slow and the graphics very slow. I thought I might add a cheap graphics card to it to see if the window graphics can be improved to usable status.
I believe an NVIDIA GeForce4 MX 440 should slot in and power up (Universal AGP).

Is a driver available that I could install that will work with this combination? (P4M266a / Ubuntu 32bit). I wonder if Compiz will throw up if I try this.
Before I buy a card, I wanted to ask here first.

Thanks

(note: [http://www.playtool.com/pages/agpcompat/agp.html#agp15vcard](http://www.playtool.com/pages/agpcompat/agp.html#agp15vcard))

---

### Post by mörgæs on 2017-03-04
Before considering hardware I suggest that you focus on software. 
Does a fresh install of Lubuntu speed things up a little?

---

### Post by SeijiSensei on 2017-03-04
If this machine wasn't doing anything at all before, I'd turn it into a server.  If you want to make an investment in it , buy some hard drives.

---

### Post by Perfect Storm on 2017-03-04
NVIDIA GeForce4 MX 440 is supported by the nvidia drivers you can get through 'additional drivers' in ubuntu.

---

### Post by michael351 on 2017-03-04
Thanks All! 

My Ubuntu install is "brand new". I have several disk drives connected which work fine. The 2D graphic windows are painful to move around. You know what I mean ... drag a window with the mouse and wait for the redraws. Adding a graphics card should take care of that.

I will get the MX 440 and load the Ubuntu additional drivers for it. It's a fun project to do.

---

### Post by mörgæs on 2017-03-04
Yes, playing around with old stuff can be a good self study. 

Just don't put a lot of money into it. An MX 440 card should be almost free by today's standards. I upgraded from one of those many years ago, probably around 2009.

---

### Post by Yellow Pasque on 2017-03-04
> **Artificial Intelligence said:**
> NVIDIA GeForce4 MX 440 is supported by the nvidia drivers you can get through 'additional drivers' in ubuntu.

False. The last version of proprietary nvidia driver that supported Geforce 4 was the 96.xx series, which will not work on any modern Ubuntu versions (not counting Ubuntu 12.04, which is going EOL next month).

The open-source nouveau driver should work "out of the box" for it, but this card doesn't have the necessary features for running Unity with acceleration, so it's still going to use your CPU for drawing operations and it's still going to be painfully slow. Xubuntu, or (Lubuntu if you have less then 2GB of RAM) is more realistic for this kind of system.

---

### Post by michael351 on 2017-03-04
> **Temüjin said:**
> False. The last version of proprietary nvidia driver that supported Geforce 4 was the 96.xx series, which will not work on any modern Ubuntu versions (not counting Ubuntu 12.04, which is going EOL next month).

The open-source nouveau driver should work "out of the box" for it, but this card doesn't have the necessary features for running Unity with acceleration, so it's still going to use your CPU for drawing operations and it's still going to be painfully slow. Xubuntu, or (Lubuntu if you have less then 2GB of RAM) is more realistic for this kind of system.

Could I install Xubuntu alongside Gnome/Unity? Will Xubuntu's desktop take advantage of the Geforce4 MX440 graphics card? The old card is cheap enough to experiment, but if it won't possibly work, then time is more valuable (although Xubuntu looks interesting). 

I'm glad I asked ...

---

### Post by Yellow Pasque on 2017-03-04
> **michael351 said:**
> Could I install Xubuntu alongside Gnome/Unity?

Yes, assuming you have enough disk space.

> Will Xubuntu's desktop take advantage of the Geforce4 MX440 graphics card? 

Yeah, Xubuntu/xfce can use 2D acceleration for window drawing. Then again, the integrated savage graphics should do some 2D accel as well, so you may want to see how xfce performs on it before buying the geforce.

---

### Post by kurt18947 on 2017-03-05
I installed an Nvidia ISA card in a machine less capable than yours. It was recognized no problem and yes I second a less graphically demanding distro. I'm partial to LXLE on low powered machines. It's mostly Ubuntu but I prefer their software defaults.  Another non-Ubuntu distro I've had good luck with on older machines and as a VM guest is mxlinux.

---

### Post by Yellow Pasque on 2017-03-05
One last thought: If you really prefer the Ubuntu/Unity desktop, it would be best to try and find a cheap geforce 6200 AGP. [https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

---

