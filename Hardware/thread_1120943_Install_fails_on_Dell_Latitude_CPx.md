---
title: "Install fails on Dell Latitude CPx"
date: 2009-04-09
forum: Hardware
---

### Post by billfreeboy on 2009-04-09
I tried installing Ubuntu 8.10 on a Dell Latitude CPX but in the moment once it's almost done loading from the CD, the loader fails and starts up the full screen terminal.
It was done with a Live CD in Safe Graphics mode.

---

### Post by billfreeboy on 2009-04-10
I was actually able to get it running in the text based installer. But it is so slow. I might have to get this Dell Fixed.

---

### Post by snowpine on 2009-04-10
Hi Bill, I have that same computer, the Latitude Cpx! It is a pretty old laptop (mine came with Windows 98!), underpowered for a modern OS like Ubuntu. First thing to check is the ram; you should get it up to 512mb (the maximum) if possible. Also, you might consider a "lighter" OS than Ubuntu. I am typing this message right now using SliTaz, and the speed is pretty good for an old laptop. I have also had good luck with Crunchbang on the Cpx, which is similar to Ubuntu but very slimmed down. Ask me if you have any questions, I am quite familiar with the hardware.

---

### Post by bd@cb8be8510 on 2009-04-29
> **billfreeboy said:**
> I tried installing Ubuntu 8.10 on a Dell Latitude CPX but in the moment once it's almost done loading from the CD, the loader fails and starts up the full screen terminal.
It was done with a Live CD in Safe Graphics mode.

I encountered the same problem. I had Ubuntu8.10 installed and upgraded to Ubuntu9.04. (I have only 256 Mb of ram!). After upgrading the pc hangs while booting up. When you specify Safe Graphics Mode one notices a screendump and segfaults. Where can I get access to this kind of dump? When I revert to the older linux-build, the laptop starts up with Ubuntu9.04!!! It looks as if they are problems with the DELL-drivers in the latest build. 

I also noticed that I cannot run the live-cd. Same problem!

---

### Post by 1915flyer on 2009-07-01
I am having exactly the same problem on an Inspiron 3700 which I believe has common characteristics with the Latitude CPx. 

Memory should not be a problem as I have 512 MB. The memory check runs OK.

Ubuntu 8.10 installs and runs OK. I tried upgrading to 9.04 and it failed. I then tried running the Live CD which failed and also installing from the Live CD and the alternate CD but both failed. The majority of the errors seemed to be segmentation faults. Problems mostly start when loading manual hardware drivers, if I remember correctly.

Somehow, I did make it through one installation, but upon reboot prior to the first run, it failed again.

I would prefer to not be stuck with 8.10 as the final installation.

Windows XP Home installed recently and ran without discernable problems.

---

### Post by markofealing on 2009-09-05
Same problem here on a Latitude CPX 500HT. I believe the issue is not unique to Ubuntu and is a problem with the way the Live! Linux CDs work with the Dell latitude C Series laptops (CPx, CPi, C600, C640 etc). I've had hanging issues on boot with Ubuntu, Crunchbang, Fedora,  Mepis 8, PCLinuxOS 2009 and Zenwalk 6.

The only way round the problem is not to use the Live CD, but to install off the alternate CD. Alternatively, if no alternate cd is available, find another computer, install off the Live CD and then either move the hard disk to your desired computer or use CloneZilla to clone the hard disk to your laptop using USB storage.

Basically, there appears to be a general bug with recent Linux Live CDs when used Series  on this series of Dell laptop. That said, Linux runs well on the C Series laptops I know I have 3 of them 2x CPx and 1x C640.

---

