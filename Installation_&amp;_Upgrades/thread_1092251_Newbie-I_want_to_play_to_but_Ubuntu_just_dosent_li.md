---
title: "Newbie-I want to play to but Ubuntu just dosent like me!"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by kchamp84 on 2009-03-10
Hi everyone, 

Sorry to make my first post so long! It has been a week now that i have been trying to install 8.04 over an entire 30gb Quantum Fireball HDD. And I believe I have made a new enemy...HAL.

I have achieved installation success after turning off the first two options of the F6 menu before loading the installer. And once, I actually visited the desktop after install and reboot. During this visit I downloaded and updated about 56 items including the proprietary drivers for my NVIDIA FX5500. Then i did the necessary reboot and have never seen the desktop again. 

The reason for this is that I kept getting hung up on "starting the HAL hald". After some research I figured out how to manually start this process, after manually starting the DBUS. 

This got me past the HAL on startup but it still freezes at different points past starting the HAL. Sometimes on Bluetooth. Sometimes on the ATD scheduler. 

I gave up, I thought that maybe the graphics driver was the problem so I wiped the system with a fresh install from the LIVE CD. No work, same problem and this time I cant even get to the login screen even once. 

I have hit a dead end in my search for answers so I'm looking for help. Thanks alot!

---

### Post by pmlxuser on 2009-03-10
well have you tried reseting the bios seeting??

differnt machines have diferent ways, i would go to bios setting and try resetiing everything to default and trying again.

by the way have you tried installing a differnt version of the ubuntu.. 
Random things sometimes work i would not have a good answer if a previous or advanced version work but its worthy a shot. ;)

---

### Post by kchamp84 on 2009-03-10
thanks, but reset had no effect. same issue. Actually I first tried 8.10 but had the same exact problem.
Could it be my vid card?

---

### Post by stanz on 2009-03-10
> **kchamp84 said:**
> thanks, but reset had no effect. same issue.
Actually I first tried 8.10 but had the same exact problem.
Could it be my vid card?

It could...
I have nvidia but don't use their drivers.
After a fresh install--graghics are slow and such--but I check the forums 
before choosing a driver.

One thing that makes it easy is using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") after I'm up and running.
Also, I do not use the livecd..I choose the alternate .ios cd, so
the only thing thats going on--is an install--lacking graphic eye candy.

---

