---
title: "Ubuntu 10.04 boot failure - Graphics Driver?"
date: 2010-05-19
forum: Hardware
---

### Post by itsllamapowered on 2010-05-19
I'm pretty new to linux and decided to try it. I installed ubuntu 10.04 using Wubi alongside windows. When I restarted after the installation ubuntu would not boot. I get lots of strange colours and lines on my screen and nothing else happens. I have tried using safe graphics mode but the problem still occurs. I believe the problem is something to do with the graphics driver. The graphics card is a Nvidia Geforce Go 7300 in a Dell Inspiron 6400.

Thanks

---

### Post by efflandt on 2010-05-19
I have never done Wubi.  But I have run 64-bit 10.04 LTS on a Dell Inspiron 6400 booted from a USB drive, and it sometimes ended up with a pattern of red (orange?) and white hash marks at the top of the screen and then seemed unresponsive.  Other times it booted fine.

It is probably related to the new kernel mode setting (KMS) video driver.  My 6400  has ATI Radeon Mobility X1300 video.  My desktop with ATI X1300 had other issues with KMS (booted fine, but sluggish at some video tasks and suspend/hibernate would hang with blank video still on).  Disabling KMS made my desktop run as fast as 9.10 and fixed its suspend/hibernate. That also seemed to fix the boot problem I had with the 6400.

Try **nomodeset** kernel boot parameter, which uses regular modules instead of kernel driver.  Or **radeon.modeset=0** is more ATI specific if you ever install it on an external drive that boots multiple computers, and only have problems with the ATI KMS.

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture")

PS: I just reread that and noticed that you have nVidia.  You might still try the **nomodeset** parameter which is general.  But the nVideo specific way has something else for the * in *.modeset=0.

---

### Post by fuzzydough on 2010-05-19
I'm having the same problem (same laptop/graphics card, upgrading from 9.10 to 10.04) & am also pretty new to linux. The nomodeset and radeon.modeset=0 kernel boot parameters (tried individually) didn't appear to change anything.

More details: I upgraded using the upgrade button in the update application. I didn't run into any problems during the process, and when it was done, it was functioning fine. Now when it boots, the white ubuntu logo comes up fine, but after a few seconds, a colored line goes through it. The screen goes black for a bit longer than usual, and then the color lines appear. After a few seconds, I can see and move my mouse pointer (which is surrounded by while lines). There's a constant blinking underscore cursor in the top left corner. The first time I booted it up like this, I issued the keyboard command to open a terminal, and saw unintelligible text and cursors scattered around but I haven't seen this on subsequent boots. Issuing the keyboard command to turn on wifi doesn't work (there's an LED light that should turn on if it's working). I also have a Windows 7 partition which is working fine.

Any more ideas/help would be greatly appreciated.

---

### Post by fuzzydough on 2010-05-22
replacing the parameters 'quiet' and 'splash' with nomodeset worked for me

---

### Post by menu on 2010-05-23
How do you do this: "Try nomodeset kernel boot parameter" and how do you make this setting permanent? 
Thank you, Menu

---

### Post by itsllamapowered on 2010-05-31
Thanks for all the help everyone!
I tried the 'nomodeset' parameter and it worked! (you open up the grub boot menu and then press the e key on the appropriate menu option, scoll down the code and carefully replace 'quiet splash' with 'nomodeset')

Just wondering now, when I start ubuntu I get the scrolling text is there any way I can get the graphic boot screen - do I need to install a driver or something in ubuntu?

Thanks

---

### Post by jrhart on 2010-06-01
Am having the same issue with gateway laptop with ATI radeon. If I boot to 2.6.31-21-generic kernel, no problem. The issue seems to be with 2.6.31-22-generic kernel. Any Ideas?

---

### Post by ioram on 2010-06-07
I used the nomodeset setting and it worked just fine (10.04, ATI).

Does anyone know how to save the change in the GRUB option where I wrote NOMODESET?

---

### Post by Tobis84 on 2010-06-27
Hi
I'm trying to boot from a USB-startupdisc instead of a LiveCD with Ubuntu 10.04 and have the same kind of strange colors after boot is done.
I don't think I have the option of doing that NOMODESET in that setting.

any suggestions?

---

