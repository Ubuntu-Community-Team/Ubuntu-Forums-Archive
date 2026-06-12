---
title: "[SOLVED] MCP67M chipset sorrows"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by lswest on 2007-09-29
hey guys,
so, i have a Compaq PC with XP/Ubuntu dual boot, no probelms there, but a while back (couple of weeks only really) i bought an HP DV6545EG laptop, and its graphics chipset is an MCP67M (supposedly similar to the Nvidia Geforce Go 7150M, not entirely sure how its diff, but hey).  I was wondering if any of you guys go it to install and run correctly in any version of Ubuntu, because i have gone through literally hundreds of Linux distros to see if i can find one that works with this graphics card, and so far only SUSE works, but it doesnt recognize any network cards, and i really just dont like SUSE.  So i was wondering if anyone got it to work with the nvidia drivers, or somehow got it to work, or if not, request that support be integrated sometime into either Gutsy or 8.04 when it eventually comes out, because i LOVE linux and so far i found Ubuntu is the best choice, because its the least amount of work to set up:P and because i like the default theme too, and besides compiling a Debian kernel and setting it up EVERY time you wanna install it is a pain in the ***.  So, any replies would be great!!!

thanks,
Lswest

*EDIT* Fixed it myself, it works now that i installed it from a safe graphics mode liveCD, using the VESA gfx driver.  Don't Know if it will work with any nv or nvidia drivers... but it works:D

---

### Post by baked on 2007-10-11
Hey,

I have this nvidia driver as well.  When I boot up with vesa, I can only use 800x600 resolution.  Are you able to get a better resolution then that?  

I am booting up off the live cd, killing GDM and forcing 1280x800 and vesa in my xorg.conf.  It boots up then, but like I said, I can only use 800x600.

---

### Post by lswest on 2007-10-12
mine runs at 1024x768 after i ran through the xserver set up again, and unchecked the 1024x768 and then rechecked it (all in the same reconfigure).  Don't know if it was luck or if that really fixes it:P but you can always try (after backing up xorg.conf) replacing the resolution lines (basically, write the same thing in, and then restart the Xserver with ctrl + alt + backspace.  Hope this works for you!

---

### Post by pizpot on 2007-10-14
I just got a HP Pavilion dv6645ca with geforce go 7150M. Comes with restore, not install vista cds. To work around, I shank the partition, and installed XP. No vid drivers on HP or nvidia. HP tech support said there will not be any coming only for vista. Whatever, I found some on softpedia I think. So moving on, to the triple part of the boot--ubuntu. 7.04, 6.10, 7.10beta5 will not install in GUI mode. What the heck. And I know the broadcom wireless will be hell too. Hello Dell I guess, goodbye HP. Remember--keep your reciept, and shop where you can return for money back.

---

### Post by lswest on 2007-10-15
Have you tried installing it in safe graphics mode?  it worked for me, and the broadcom is a pretty simple workaround too (ndiswrapper the drivers)

---

### Post by scizmeli on 2007-12-04
Hello,

I have the same problem here too. I installed Gutsy on the safe graphics mode. Then I installed Automatix2 which installed the nvidia-glx-new package. I have the 3-D effects now but cannot obtain a better resolution than 800x600.

lswest, what tool did you use when you configured the x-server and checked on-and-off the 1024x768 option? I'd like to try that trick.

Also, I was able to boot the laptop with the newest knoppix cd which was able to provide a better  resolution than 800x600. I think that the solution we are after lies on that CD. I could make a test and get you the related info on what knoppix uses as driver but I would need your guidance on that. What should I look for when I boot with knoppix?

let's solve this

---

### Post by lswest on 2007-12-05
well the command i used to re-configure the screen resolution was "sudo dpkg-reconfigure xserver-xorg"  and the other option to try would be to use the nvidia control panel (i believe the package is nvidia-setting). i'm pretty sure that it will work (my resolution is actually at 1280 x 800 atm, thanks to the nvidia control panel.  it's basically the same as the nvidia control panel in windows, giving you options to change the graphics.  hope it solves your problem.  I think this is more a bug than any problem with software, so we should try to solve it before having a look at knoppix.

---

### Post by lduperval on 2007-12-07
I managed to install the latest Nvidia driver and my X now displays in 1200x800.

To install, I followed the instructions here: 

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Basically, I made sure I had a vesa system working, then I followed the steps one by one. It worked great.

I downloaded the latest binary drivers from Nvidia to make it work. I have enabled the desktop effects (I'm on Feisty) and they work, although I find them kinda slow. I'm able to play some 3d games, so it seems to be working better than my previous laptop.

The driver I installed was NVIDIA-Linux-x86_64-100.14.19-pkg2.run.

L

---

