---
title: "No screens found error"
date: 2008-11-30
forum: Hardware
---

### Post by tazza on 2008-11-30
I'm having problems installing ubuntu onto my Toshiba laptop. It has windows vista already installed on it (I was hoping to partition it).

I am booting off the ubuntu CD: "Ubuntu 7.04 (Feisty fawn) PC Desktop CD 15 April 2007"

When I go through the install process after some blinking of screens I get a blue screen with a message talking about an Xserver problem. The error message is

No devices detected
Fatal Server error:
    no screens found

and then leading to a console with ubuntu@ubuntu:

I followed their advice and went here: [http://wiki.x.org/wiki/FAQErrorMessages#head-93b1e0b56f76546d61364f789045e9c745b6cfd4](http://wiki.x.org/wiki/FAQErrorMessages#head-93b1e0b56f76546d61364f789045e9c745b6cfd4)

but xorgcfg didn't seem to exist and I tried using X to no avail.

The log file /var/log/Xorg.0.log contained the lines:

(--) PCI: (0:2:1) Intel Corporation unknown chipset (0x2a42) rev 7, Mem @ 0x50000000/22, 0x40000000/28, I/O @ 0x5110/3

(--) PCI: (0:2:1) Intel Corporation unknown chipset (0x2a43) rev 7, Mem @ 0x53500000/20

among many others. I was hoping to copy the config file but the USB connection doesn't seem to work. 

Does anyone know what to do to fix this problem? Or know of any number of general strategies to try? I don't have a network cable at the moment but could get one if it is needed. (ie if apt-get is required)

I don't know the exact system specifications but if you could tell me where to look i could try to dig them up.

Thanks in advance

---

### Post by lotacus on 2008-11-30
if your using 8.10, when you get to the ubuntu menu screen, start the recovery mode, ubutu will detect the no screens error and will prompt if you want it to try and fix xorg. Select yes, and it will reconfigure xorg.conf. I had to do this once and it worked and I was glad!

You can also try going to the X11 directory and rename xorg.conf to xorg.bak and then find another xorg file ie: xorg.orig and rename that to xorg.conf and things should be fine.

The only other time where Linux wouldn't detect a screen was when the kernel just didn't support it and that was another distro. Ubuntu always supported all of my graphic cards and laptops.

When your applying commands you need to be aware that X is different than x. The case matters. xorg does exist but it's not xorgcfg. It's xorg.conf.

---

### Post by tazza on 2008-11-30
> **lotacus said:**
> 
You can also try going to the X11 directory and rename xorg.conf to xorg.bak and then find another xorg file ie: xorg.orig and rename that to xorg.conf and things should be fine.


I looked in the X11 directory but I couldn't find any alternate xorg files. Are these kept somewhere else?

Also I only have ubuntu 7.04 which doesn't seem to have recover mode on the initial menu. Is there an equivilant commandline order that I could use for the older version?

---

