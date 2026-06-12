---
title: "Flickering bootscreen and cant login. HELP."
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by litium on 2009-10-05
Hi, i installed 9.10 alpha 3 today and things dind-t go well at all. Fist, whenever i try to boot, the screens starts to flicker like crazy, and it asks me to login (no interface at all, just command line). When i try to input something, its really hard beacuase it flickrs and the keyboard respond to this flickering also, making it very hard to type. Also, my windows partition cant be loaded from the grub. Is there any way to repair this from the liveCD... thanks in advanced.

---

### Post by vpram86 on 2009-10-08
@Litium
I am also experiencing it :(. I removed older kernels as well! So could not login to Ubuntu.I upgraded directly from Update Manager and its will latest updates now, i guess.

---

### Post by caeroe on 2009-10-08
> **litium said:**
> Hi, i installed 9.10 alpha 3 today and things dind-t go well at all. Fist, whenever i try to boot, the screens starts to flicker like crazy, and it asks me to login (no interface at all, just command line). When i try to input something, its really hard beacuase it flickrs and the keyboard respond to this flickering also, making it very hard to type. Also, my windows partition cant be loaded from the grub. Is there any way to repair this from the liveCD... thanks in advanced.

Are you guys Nvidia users?  2.6.31-12 and 2.6.31-11 are flickering.

I have to stay with 2.6.31-10.  Running 9.10 x64 with a 8800GT card.

I've done manual driver installs many times before, I'm sure I'm doing it right.  Ubuntu's utility fares no better.

---

### Post by elitenoobboy on 2009-10-09
> **caeroe said:**
> Are you guys Nvidia users?  2.6.31-12 and 2.6.31-11 are flickering.

I have to stay with 2.6.31-10.  Running 9.10 x64 with a 8800GT card.

I've done manual driver installs many times before, I'm sure I'm doing it right.  Ubuntu's utility fares no better.

Only 2.6.31-12 is flickering for me with my 7950gt. -11 still works.

---

### Post by vpram86 on 2009-10-09
Yes i have nVidia 6150 with my HPtx2000z
Indeed it was the realted to nVidia module.

I use the latest 2.6.31-12-generic and all works fine (did not test wacom yet)
I booted into revoery mode, changed Driver name in /etx/X11/xorg.conf from nvidia to nv!
Hope it helps!

Edit: Today updated to 13 and it reverted driver name to nvidia again! So was not starting at all. Again renamed dirver to nv and then it worked
Also wacom works ootb without me actually doing anything. Ubuntu Rocks!

---

### Post by caeroe on 2009-10-09
> **vpram86 said:**
> Yes i have nVidia 6150 with my HPtx2000z
Indeed it was the realted to nVidia module.

I use the latest 2.6.31-12-generic and all works fine (did not test wacom yet)
I booted into revoery mode, changed Driver name in /etx/X11/xorg.conf from nvidia to nv!
Hope it helps!

Edit: Today updated to 13 and it reverted driver name to nvidia again! So was not starting at all. Again renamed dirver to nv and then it worked
Also wacom works ootb without me actually doing anything. Ubuntu Rocks!

Well ok, I modified xorg.conf in recovery mode.  So I'm back in kernel "13".

However trying to exit out and install Nvidia drivers is impossible, I get a bunch of funky colors and lines.  I can't really describe, I never saw such a thing in years.  I'm now forced to use the 185 series drivers from Ubuntu's Hardware Drivers utility, maybe that'll work.

Edit:  Nope.  I'm unable to install any drivers on any kernel revision higher than 2.6.31-10-generic, manually or through Ubuntu's utility.

---

### Post by vpram86 on 2009-10-10
Interesting. Exactly as you described, i got those lines :)
But thats when i upgraded to kernel 13 immediately it replaced Driver name. After then only, i went back to 13's recovery mode and edited Driver name. After that funky lines came, but in 5-10 secs, normal boot will continue.
I use 185 series drivers form Hardware Drivers. And i installed/uninstalled it from command line many times. 
Using apt-get install nvidia-glx-185 and apt-get remove nvidia-glx-185. it will automatically download from linux-resticted-modules.

---

### Post by 10Digits on 2009-10-10
As, Artificial Intelligence told me....

These are in alpha version so it is possible that they may not support or might cause problems on some hardwares....so it is best to be patient and use the public release instead.

As for your problem ,I guess,You already know that the problem might be because of ubuntu not recognizing your gpu.

---

### Post by bigbossbing on 2009-11-02
This issue is still prevalent in the 9.10 public release with nvidia cards and the latest nvidia proprietary drivers.

This is my first time with linux and Ubuntu. Prior to running the installation from liveCd, i had upgraded the driver (ubuntu had asked, so i said yes. There was no issues running liveCd post driver upgrade).

When booting in recovery mode, the CLI does not flicker, i can log in ok. But as i am new to linux, i dont know what command to type to then start ubuntu lol

In normal startup mode, the flickering is so intense that keystrokes are often not recognised by the CLI, making typing your password impossible. 

Has a concrete solution been found yet?

thanks

---

### Post by Sunflower1970 on 2009-11-02
Check this thread out: [http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459) 

There are multiple solutions to fix the flickering from...well you know... If one doesen't work, just try another. 

:)

---

