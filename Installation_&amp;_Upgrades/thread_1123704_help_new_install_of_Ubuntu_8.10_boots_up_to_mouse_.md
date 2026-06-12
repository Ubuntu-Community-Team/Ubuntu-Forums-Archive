---
title: "help new install of Ubuntu 8.10 boots up to mouse and wallpaper only"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by mrq201 on 2009-04-12
Ok, i have a strange problem. I downloaded ubuntu 8.10 onto a cd, so I am guessing I have a live cd. I installed ubuntu onto an 80 gig harddrive using a Dell optiplex GX170 i believe. The specs on that computer was P3, 512 ram. Everything was installed ok and perfectly on the harddrive.

I brought the harddrive home, and hooked it up to my dimension 2400 which has 1.5gb of ram p4. 2.8GHz. I got to the screen where I had to input my username and password, after I did that, the only thing i saw was the mouse pointer, and that background wallpaper.

I proceeded to reinstall it unbuntu from the live CD, but that did not work either.

I know the cd is not defective because I ran the tests.

Any help or advice would be appreciated. If anymore information is needed from me, I would be glad to assist you with it

---

### Post by imperial07 on 2009-04-16
I am having the exact same issue.  I dont know how much Linux experience mrq201 has, but I am a complete noob, so any help would be much appreciated.

---

### Post by mor377 on 2009-04-16
yup... im ditto on that one... like it just freeses... but then again im running it on a 512 mb of ram computer as well... so im thinking ubunto dosnt like 512 hahaha

---

### Post by PsychoJosh on 2009-04-16
I had the same issue...I just down loaded 8.04, and that worked great for me.

I'm using a  P4 2.4 gz, 512 mb ram, 250 gig hard drive, and Asus mother board.

Works great with 8.04...

..but, 8.10 just gives me a mouse pointer.

---

### Post by imperial07 on 2009-04-16
I just fixed mine, found instructions on another site.  Here is what I did:

Before logging in click on Options in the lower left corner
Choose Select Session...
Choose Failsafe Terminal

Log in.

In the console that opens up type:
sudo apt-get update

When the updates have finished downloading type:
sudo apt-get dist-upgrade

After they updates have finished installing type:
sudo reboot

Hope that helps you guys.

---

