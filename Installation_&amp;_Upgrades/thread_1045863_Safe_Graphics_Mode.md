---
title: "Safe Graphics Mode"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by NuttyMonk on 2009-01-20
Hi all,

i'm very new to Ubuntu and Linux in general. I've installed Ubuntu but it won't load past the login screen. I either get a black screen or the screen stays pink/cream.

I've used the Live CD to boot Ubuntu in Safe Graphics Mode and it loads OK (from the CD, not using the install on the hard disk, i can't figure out how to load that using Safe Graphics Mode).

The fact that Ubuntu can load from the CD in Safe Graphics Mode, but can't load from the install on the hard disk means that the problem must be with some of the boot options in the hard disk, probably graphics options.  Hopefully if i can see the difference in the boot options then i will be able to change the options for the standard boot and get Ubuntu running off my hard disk, rather than the CD.

Can anyone tell me where i find out this info and how to go about changing the options for the standard boot?  Bearing in mind that i'm a complete noob with Linux and Ubuntu.

Cheers

NM

---

### Post by alan34 on 2009-01-21
When the computer first starts you will see a menu appear on the screen something like this -


Ubuntu 8.10, kernel 2.6.27-11-generic
**Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)**
Ubuntu 8.10, memtest86+

Cursor down to recovery mode option and press enter.
This will take you to a menu with about six options.
Pick the one **Xfix** this should get your graphics back
(bottom option). Then reboot.

Note if it gives you the option of picking which graphics
driver to use pick the **vesa** option even if you have
a ATI or Nvidia graphics card.

To install ATI/Nvidia cards when you have your desktop back 
Go - System - Administration - Hardware Drivers and you
should be able to download and install there.

---

### Post by NuttyMonk on 2009-01-21
> **alan34 said:**
> 
Cursor down to recovery mode option and press enter.
This will take you to a menu with about six options.
Pick the one **Xfix** this should get your graphics back
(bottom option). Then reboot.

Thanks for your reply Alan.

After doing the Xfix you say i should reboot.  Does this mean i should choose the 1st option in the menu which has Xfix in it?  I think it says "Resume Normal Boot"  or should i do something else?  I've tried different ways of rebooting as you've said but with the same results as before.  I also never get asked what graphics drivers i'd like to use.

I've installed Ubuntu on a 2nd hard disk in a dual boot with Windows XP.  I've downloaded the Linux drivers for my graphics card (although they were made in 2004 i think) and i was wondering if there was any way i could install them when i'm logged into XP and not Ubuntu, or if i can look at the info in the drivers to see what settings i should use in the boot config for Ubuntu.

Cheers

NM

---

### Post by alan34 on 2009-01-23
Hi sorry for the delay. First you cannot install the Linux drivers from XP and you should install the drivers using Synaptic Package Manager once you have ubuntu up and running.

Could you try this - boot to recovery mode again and pick drop into a root terminal shell.

then enter this

sudo dpkg-reconfigure -phigh xserver-xorg

This should reconfigure your graphics.

---

### Post by NuttyMonk on 2009-01-24
Hi alan,

thanks for getting back to me about this.  I tried what you suggested and rebooted once i'd typed in the command you gave me but it still didn't help.

I'm getting my new PC parts on Monday and was trying out Ubuntu to see if i wanted to install it as my default OS before i set up my new PC.  I think i like the look of it anyway, despite the problems i've had with the onboard graphics on my very old motherboard so i'll just wait till Monday and install it then. My new motherboard has a more up-to-date graphics card on it so i shouldn't have any probs.

Thanks for you advice anyway.

Cheers

NM

---

