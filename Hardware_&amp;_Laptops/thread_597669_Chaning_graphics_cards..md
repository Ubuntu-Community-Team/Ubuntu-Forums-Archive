---
title: "Chaning graphics cards."
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by waspinator on 2007-10-30
Hi,

I've looked around but couldn't find what I was looking for. I hope someone here can help me.

I'm using Ubuntu 7.10 Gusty

I've got a desktop computer that has a Radeon 9600, but since the ATI drivers are no good, it runs like poo. Now I'd like to switch out my Radeon for a GeForce 5200. I know its 'worse' but it works better with Ubuntu for me. Both cards are AGP. 

The computer I want to do this on is my computer i work on, so before I did anything I tried to recreate a similar scenario on another computer. I had the GeForce 5200 there, and I replaced it with a Radeon 9200. That didn't work out too well. I got a message about Ubuntu running in low graphics mode, but I couldn't configure it to use the Radeon properly. 

Now I want to switch out my 9600 for the 5200, but I'm afraid that ubuntu isn't smart enough to know what to do after this change. Is there some way of guiding Ubuntu along so that it doesn't screw up my computer? 

And I really don't want to reinstall ubuntu just for this graphics card. I remember when I used windows, and did this sort of thing there wasn't any problem. All I would have to do is uninstall the ATI drivers, swtich cards, and then install the nVidia drivers. I hope/wish Ubuntu can do something similar. 

Thanks,

Waspinator

---

### Post by aoanla on 2007-10-30
I think that your plan should work - although, I'd be inclined to install the nVidia drivers /first/, then switch cards. That way, your xorg.conf should be configured to load the nvidia driver from the start, rather than potentially getting confused by trying to load the fglrx driver for an non-existent ATI card...

In any case, once you've got the nVidia drivers installed, removing the ATI drivers should be easy and should ensure that there's no niggling conflicts in the kernel (not that there should be, but...)

---

### Post by waspinator on 2007-10-30
Would I have to run dpkg-reconfigure -phigh xserver-xorg to reconfigure it?

I may install ubuntu on another hd, and try to upgrade on there before I do it on my actual HD.

I wish I knew how linux does things better, so I could fix things once they go wrong. I usually just resort to reinstalling everything if anything breaks.

---

### Post by aoanla on 2007-10-31
> **waspinator said:**
> Would I have to run dpkg-reconfigure -phigh xserver-xorg to reconfigure it?

I may install ubuntu on another hd, and try to upgrade on there before I do it on my actual HD.

I wish I knew how linux does things better, so I could fix things once they go wrong. I usually just resort to reinstalling everything if anything breaks.

As far as I know (and it has been a while since I installed the nVidia drivers), it should be possible to get the installer to write you a new xorg.conf, without rerunning dkpg-reconfigure.
You might want to read all the installation notes for the current nVidia driver, to be sure of the details.

---

### Post by waspinator on 2007-11-01
Well I did as you said.

- Installed the nVidia driver from Add/Remove Programs
- Changed Graphics cards
- Ubuntu started up in 'low graphics mode'
- I selected to configure, and selected the nvidia driver
- Rebooted, and then it asked me if I wanted to use the restricted driver
- Rebooted again. Graphics worked

But then for some reason my Ethernet card eth0 disappeared. So I shut down, took it out, rebooted without it in. Then shut down again, and replugged it back, and it worked again. Strange, but everything is working now. :) 

Thanks for your help

---

