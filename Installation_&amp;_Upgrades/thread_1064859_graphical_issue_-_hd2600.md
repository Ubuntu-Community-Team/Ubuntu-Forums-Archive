---
title: "graphical issue? - hd2600"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by Spiriteh on 2009-02-09
Hi, I'm trying to install Ubuntu 8.10 however when I get to the installer (well X) the screen is blurred and unusable, I have tried booting with 'live-install vga=771(2? can't remember to be honest) fb=false' however I get the same issue.

Is there a known problem with the HD2600XT/ HD2600 series and if so are there any fixes? 


Thanks
SpiriteH!

---

### Post by yankeeDDL on 2009-02-10
Hello,

I have Ubuntu 8.10 and an HD2600XT.
I installed both 32bit and 64bit versions of Ubuntu: I had several problems with the drivers but never what you are seeing.

Not sure what your options are: if you can do a clean install, then stick first with Ubuntu drivers (no 3D acceleration).
If you need 3D acceleration (you will need it for any desktop effect, like Compiz) then I strongly suggest you install the proprietary drivers developed by the Ubuntu community.
Do not install (or at least I strongly suggest you don't) the "latest" drivers from AMD/ATI website.

In my case I only had a problem with video playback flickering like crazy. In the end, you just need to re-direct the output to X11 (instead of "default") and the problem was fixed for me.

If you can't re-install, then I suggest you disable all desktop effects, maybe even disable Compiz, and then try debugging.

I hope this helps.

---

### Post by yankeeDDL on 2009-02-10
By the way, perhaps you can post your HW configuration (especially, which motherboard) to see if we can have any hint of what may be happening.

---

### Post by Spiriteh on 2009-02-10
First off thanks for the input, second off here is my system spec also I get this problem when X loads for the first time in the installation stage; AMD Athlon 64 X2 5200+ Brisbane, MSI K9A Platinum Crossfire, Corsair XMS2 PC2-6400C4, sapphire HD2600XT (PCIe), Hitachi Deskstar P7K500 320GB SATA-II 16MB Cache.

Could the issue be fixed using another install method followed by installing the correct drivers later on?


SpiriteH!

---

### Post by yankeeDDL on 2009-02-10
Spiriteh, I'm fairly new to Ubuntu and haven't run into this problem.
Seems to me that you need to boot ubuntu into safe mode and then modify the configuration of the window-manager.

To boot into safe mode I suggest you look at this thread:
[http://ubuntuforums.org/showthread.php?t=438486](http://ubuntuforums.org/showthread.php?t=438486)

Then you migth look into different causes for the blurry-ing.
Here's a thread which covers quite a few options:
[http://ubuntuforums.org/showthread.php?t=464907](http://ubuntuforums.org/showthread.php?t=464907)

Are you using an LCD display or a classic CRT monitor?
Is everything blurred or only the text?
Also, if you use other OS (maybe you're trying to dual-boot with Windows): is everything working OK?

I have the same exact card: HD2600XT (PCIe) and apart from some flickering of the videos (fixable) I did not have any blurriness.

---

