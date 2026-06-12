---
title: "Installing Ubuntu with GeForce 8800"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by chiklit on 2006-12-30
I'm trying to install Ubuntu on my desktop with a GeForce 8800 GTX. I expected there would be graphics issues since even the XP drivers for it don't work all that well, but since there are linux drivers for it I thought there might yet be some hope.

Anyway, when I try to boot to the live CD it'll boot Ubuntu and then try to start X but it always crashes with the error "No screens found." Even under safe graphics mode.

Is there anyway around this without having to swap graphics cards whenever I want to boot Ubuntu?

System specs:
**CPU:** Intel Core 2 Duo R6400 (Overclocked - 2.8GHz) | **Mobo:** EVGA nForce 680i SLI | **GPU:** XFX nVidia GeForce 8800 GTX 768mb GDDR3 | **Memory:** 2gb DDR2 PC5400 667MHz Dual Channel | **PSU:** Antec Neo HE 550w | **Sound:** SoundBlaster X-Fi Xtrememusic | **HDD:** 950gb total SATA3

---

### Post by taurus on 2006-12-30
Try using the alternate CD version since it uses text based installer.  Even with text based, it's real easy to follow...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso)

---

### Post by chiklit on 2006-12-30
Thanks, that worked fine.

I never though being able to install nVidia's drivers from the terminal only would be useful until now. :P

---

### Post by taurus on 2006-12-31
You can do a lot from a terminal...  ;)

---

### Post by guarnibl on 2007-03-06
Sorry for digging up an old thread -- do we have any updates if the Feisty installer works (graphical mode) on these cards?

Did you guys get beryl working or cedega? I.e., how do games run, etc.

---

### Post by Data-Base on 2007-03-10
> **chiklit said:**
> Thanks, that worked fine.

I never though being able to install nVidia's drivers from the terminal only would be useful until now. :P

can you explain how you did install it ?

I have the same problem with the same card and a 22" screen

I installed the Alt. CD but what is next ? how to install the drivers from the terminal?

Thank you

---

### Post by mitch1200 on 2007-03-28
Have you had any success? I haven't been able to get my EVGA 8800 GTS board to be recognized. And have had no success in loading drivers. The screen just stays black.

Mitch

---

### Post by frenzie on 2007-04-03
check out [https://launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/91556](https://launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/91556)

im looking to buy this card, so im doing some research on its use with ubuntu before i go and get one!

---

### Post by cmezak on 2007-04-11
I'm having a related issue.  I've installed ubuntu and nvidia-glx, but when xserver starts my screen goes blank.  I'm running a geforce8800gts and an apple cinema display.  I've gone through dpkg-reconfigure xserver-xorg a number of times but nothing I do gets it working right.  Any tips?

Thanks!

---

### Post by cmezak on 2007-04-12
Well, I've solved my issue.  Downloading the nvidia 9755 drivers with wget from a url I got by visiting their website on a different machine, then installing them did the trick.  I had to install libc6 first, but now I'm up and running fine!  I just hope nvidia gets their drivers up to snuff soon so that I can run beryl comfortably.

---

