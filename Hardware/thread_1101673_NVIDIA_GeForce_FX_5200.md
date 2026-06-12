---
title: "NVIDIA GeForce FX 5200"
date: 2009-03-20
forum: Hardware
---

### Post by TheSurvivor on 2009-03-20
I am trying to use my PCI graphics card on Ubuntu 8.10, but for some strange reason, if I plug it in, my computer pauses less than 25% through boot up, and stops. If I use my integrated video, it boots up normally, but I'd rather have 256 megs instead of 8. I think it may be the drivers, so I am trying to install the NVIDIA drivers, but I continue to get error after error throughout install. I keep closing my X server, and trying my luck, but always get something about the drivers not being able to make a kernel, or nvidia.ko errors. Can anyone help? I've tried google, but all I found was a whole bunch of people asking this same question. Please guys I want to use my $60 card here!

---

### Post by taurus on 2009-03-20
If you want to use that add-on nvidia card, you should go into the BIOS and turn off the onboard integrated graphic controller.

---

### Post by TheSurvivor on 2009-03-20
> **taurus said:**
> If you want to use that add-on nvidia card, you should go into the BIOS and turn off the onboard integrated graphic controller.

Thanks for the tip, but I have used this card on Windows, and ubuntu 8.04. I know how the BIOS settings are supposed to be, and they are set as they are supposed to be, but it still continues to do as mentioned before.

It makes it to the Ubuntu boot screen, then stops. I believe this is more to do with Ubuntu than BIOS.

---

### Post by norwoods on 2009-03-21
have you tried installing the nvidia driver with envyng?

---

### Post by JBetts on 2009-04-27
Is there any resolution to this issue ? 

I am having the same exact problem. 

I am running a d945gcl mobo, and it works fine until I physically insert the GeForce 5200. Then it goes into kernel panic (tty1 respawning too fast, etc.). 

With the card in place, I can't even boot into recovery mode to try to manually install NVidia drivers.

When I remove the card, the NVidia driver installer (and Envy) both say that no card is discovered so no driver can be applied. 


I finally tried just compiling the kernel from scratch for my system by running it as a live CD with the PCI video card in place. Still same kernel panic/crash. 

I've pored over forums for a resolution to this issue. Found plenty of methods to install the proper drivers for the 5200 (when inserting it doesn't cause the system to crash), but never any resolutions to the kernel panic problem. 


Please help!


See previous (unresolved) posts:

[http://ubuntuforums.org/showthread.php?t=993518&highlight=geforce+5200+kernel](http://ubuntuforums.org/showthread.php?t=993518&highlight=geforce+5200+kernel)

[http://ubuntuforums.org/showthread.php?t=218761&highlight=geforce+5200+crash](http://ubuntuforums.org/showthread.php?t=218761&highlight=geforce+5200+crash)

---

