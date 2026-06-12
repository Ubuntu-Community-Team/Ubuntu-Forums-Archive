---
title: "Intel wifi link 1005 &amp; jolicloud 1.2"
date: 2011-11-25
forum: Hardware
---

### Post by rrgjl on 2011-11-25
Hi,

Just recently I started using Jolicloud on my *Acer Aspire One Happy 2* netbook.
Installation was smooth, and everything is working just fine, except for my wireless card. The whole idea of the netbook is kind of diminished when I'm connecting it through RJ45 ;) So I'd like to get this fixed.
The wireless card is an Intel wifi link 1005.

I have been looking around, and firstly seemed to have found the drivers, which I supposedly only needed to copy to lib/firmware. I did this, rebooted, but no luck. Still not working.
Then I found some steps telling me to download compat-wireless drivers and 'make' and 'install' them. However, when i try to 'make', it is giving me an error saying 
```
ERROR: your kernel has CONFIG_CFG80211=y, you should have it CONFIG_CFG80211=m if you want to use this thing.
```
As you may have already noticed I'm quite the noob when it comes to Linux, so I have no idea what to do next. I'm pretty sure Jolicloud is Ubuntu-based, but as it seems the drivers are 'baked' into the kernel or something, I really don't know how to proceed from here.

---

### Post by rrgjl on 2011-11-25
Ok I have found that I may have to recompile my kernel to be able to add drivers? 

I found this forum post in response to someone with a similar question:

> I would say you can't use compat-wireless because wireless drivers are built in the kernel (= are not modules). You have to recompile with the option CONFIG_CFG80211 set to module.

Is this correct, and if so, how do I go about this? Of course I could just look up how to recompile, but I'm a little hesitant as I don't know what I'm doing exactly, so I'd like some confirmation.

---

### Post by rrgjl on 2011-11-25
Okay! So the noob fixed it himself. Turned out 'all' I had to do was update the kernel. Kernel 2.6.37 and up support my wireless chip, and the 2.6.35 kernel which I was using did not. I don't know if this is the best way, but as I couldn't get it to update to a newer version through the console, I simply followed the following steps from [http://www.ramoonus.nl/2011/03/linux-kernel-2-6-38-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/03/linux-kernel-2-6-38-installation-guide-for-ubuntu-linux/)

```

1. Download the kernel headers package;
linux-headers-2.6.38-020638_2.6.38-020638.201103151303_all.deb

2. And the appropriate package for your system
I386: linux-headers-2.6.38-020638-generic_2.6.38-020638.201103151303_i386.deb
AMD64: linux-headers-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb

3. And the accompanying compiled kernel;
I386: linux-image-2.6.38-020638-generic_2.6.38-020638.201103151303_i386.deb
AMD64: linux-image-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb

Install the files in the same order (else it won`t work!)

In the terminal run:
sudo update-grub
Reboot and select the kernel from the bootloader menu
If it`s not there check all steps (and of course errors)
```

---

