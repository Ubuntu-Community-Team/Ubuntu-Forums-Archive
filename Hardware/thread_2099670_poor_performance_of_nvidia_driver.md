---
title: "poor performance of nvidia driver"
date: 2012-12-30
forum: Hardware
---

### Post by Chogan on 2012-12-30
i have a hp pavilion dv2500 notebook with nvidia Geforce 8400M Gs as graphic card. 
i installed ubuntu 12.04 on it. everything is ok but nvidia driver. 
when i installed nvidia graphic driver, performance reduced: unity became slow, firefox scrolling became slow and same thing happened for pdf reader. also boot time is longer. 
i never had such a expectation, in fact my expectation was completely vise vera. i expected nvidia driver performance be better than nouveau. 
now i'm using nouveau. in unity 2d it is ok but i cannot use unity 3d using nouveau in ubuntu 12.04. 
who know what is the problem with my nvidia graphic driver? how can i solve that?
i installed that using "Additional Drivers".
i had same problem with nvidia driver in openSUSE also.

---

### Post by Pjotr123 on 2012-12-30
Which version of the restricted nvidia driver did you install? There are several versions available in the repositories.

---

### Post by Chogan on 2012-12-30
i cannot remember the exact version number. but i dare say i tried several nvidia versions in ubuntu and openSUSE and all of them caused to this problem.

---

### Post by Pjotr123 on 2012-12-30
You can check the version if you install Synaptic:
```
sudo apt-get install synaptic
```

You can use Synaptic for changing the driver. First try nvidia-current, then nvidia-173, then nvidia-current-updates and maybe finally even nvidia-experimental-304 and nvidia-experimental-310.

Stay with the driver that performs best, and only try the experimentals if there is really no good alternative.

If you lose display because of a driver change, you can repair it as follows:
[https://sites.google.com/site/easylinuxtipsproject/display#TOC-Major-problems-no-graphical-display-at-all-](https://sites.google.com/site/easylinuxtipsproject/display#TOC-Major-problems-no-graphical-display-at-all-)
(item 1, left column)

---

### Post by Chogan on 2012-12-31
as i explained, its several mounts that i using free open source driver (nouveau).
i tested both current and experimental nvidia drivers in ubuntu and openSUSE and i had the problem in all situations. 
it is useful if look at my description about this problem in openSUSE forums too. here is **[the address]("https://forums.opensuse.org/english/get-technical-help-here/hardware/471067-nvidia-driver-slower-than-open-source-driver.html")**.

---

### Post by Pjotr123 on 2012-12-31
It appears to be a 5 year old computer, with an Nvidia card that has only 64 MB dedicated RAM. You shouldn't expect too much 3D performance...

I advise to install the Nvidia restricted driver again (the one Ubuntu advises is best, probably in your case the "current"), and stay with a 2D desktop. Like Unity 2D, or even better: my own personal favourite Xubuntu:
[https://sites.google.com/site/easylinuxtipsproject/xubuntu](https://sites.google.com/site/easylinuxtipsproject/xubuntu)

You can even transform your existing Ubuntu installation into Xubuntu:
[https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative)

If you apply some speed tweaks, your computer will fly:
[https://sites.google.com/site/easylinuxtipsproject/speed](https://sites.google.com/site/easylinuxtipsproject/speed)

Afterwards, test the performance (FPS rate) of your Nvidia like this:
```
glxgears
```
(you may need to install mesa-utils first)

Good luck and happy 2013! :)

---

### Post by Chogan on 2012-12-31
Thank you for your advise. but my laptop had a windows vista pre installed on it. and as you may know, windows vista is one of the heaviest OSs in th world but my laptop worked with vista very good. for this reason i expect ubuntu to be better than vista.

---

### Post by Chogan on 2012-12-31
now, i'm using free graphic driver nouveau and resault of glxgears is:
```
~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
1454 frames in 5.0 seconds = 290.694 FPS
1441 frames in 5.0 seconds = 287.970 FPS
1566 frames in 5.0 seconds = 313.090 FPS
1737 frames in 5.0 seconds = 347.173 FPS
1766 frames in 5.0 seconds = 353.095 FPS
1869 frames in 5.0 seconds = 373.749 FPS
1490 frames in 5.0 seconds = 297.719 FPS
1726 frames in 5.0 seconds = 345.159 FPS
1696 frames in 5.0 seconds = 339.111 FPS
1705 frames in 5.0 seconds = 340.881 FPS
1610 frames in 5.0 seconds = 321.970 FPS
1447 frames in 5.0 seconds = 289.094 FPS
1473 frames in 5.0 seconds = 294.442 FPS
1449 frames in 5.0 seconds = 289.668 FPS
1449 frames in 5.0 seconds = 289.714 FPS
1465 frames in 5.0 seconds = 292.847 FPS
1469 frames in 5.0 seconds = 293.660 FPS
1520 frames in 5.0 seconds = 302.526 FPS
1299 frames in 5.0 seconds = 259.716 FPS
1464 frames in 5.0 seconds = 292.703 FPS
```is it normal? if i install nvidia graphic driver, will it improve?

---

### Post by mbuell on 2012-12-31
I am having very similar problems with a Toshiba Tecra M11, intel I-5, with an Nvidia graphics chip using shared memory. My machine ISN'T 5 years old, but I also think that thought misses the point, and misses the problem. 

Eg: My toshiba worked great, including 3-D, with the nvidia proprietary drivers, for 10.04. Today, I give ubuntu a fail on this machine and 12.04. I COULD go back to 10.04, but hey! 10.04 is about to run off support! 

Unity and 12.04 have messed with the nvidia support. I do NOT know yet what is going on - as I am still involved in trying to make my machine productive again. I tried 12.04 Unity, and xfce - 3-D and dual monitor situations were messed up. So now I'm trying Mint to see if maybe leaving Unity out of the equation might help. 

Since my nvidia chip is pretty new, I tried the "current" version, and the latest available from nvidia, and another one in between those two. Nvidia is aware that there is a problem generated by 12.04 (and 12.10), and worked up a couple of beta issues to try and deal with it. They improved matters, but didn't fix them. Nouveau is about the same-- it is useable, but no 3-D, and no dual monitor desktop extension. 

Sorry to say I can't offer solutions. But, I can tell you that you are not alone. Keep posting. Maybe you will be the one to solve the problem.

---

### Post by Chogan on 2013-01-06
How can i find if my graphic card of my laptop supports hardware acceleration or not?

---

### Post by Calinou on 2013-01-06
> **Chogan said:**
> How can i find if my graphic card of my laptop supports hardware acceleration or not?

Any graphics card does...
Anyway, use the proprietary driver if you want performance and OpenGL support of latest versions (3.3.0 or 4.3.0 depending on your hardware).
Or, use the open source driver which respects standards more, but is much slower and uses more electricity.

If you want better game performance you can try using Xfce instead of Unity, and disable the desktop effects.
```
sudo apt-get install xubuntu-desktop
```

tip: if you want to buy a computer sooner or later, buy a desktop. They are much faster and last longer (less risks of overheat).

---

### Post by mdrag13 on 2013-11-03
Hi,

I've been using Ubuntu for a couple of years on a PC that is not "the last state of the art" machine (aprox. +3y old). Since the Unity first appeared I've had problems with graphics rendering which resulted in a slow (and occasionally unresponsive) 3D GUI (switching to Unity 2D made things a lot better). My config is the following:

MSI K9N6PGM2-V2 MBO
AMD Athlon II X2 240 @ 2.8GHz
2 GB TakeMS DDR2 @ 800MHz
500GB Western Digital WD500AAKS HD
NVidia Geforce 6150SE nForce 430

I've tried instaling various NVidia drivers (via Ubuntu's drivers repo and manually from NVidia website), changing graphic settings and a lot of similar experiments but nothing helped - 3D Unity was simply slow and lagging. As you can see, my graphic card isn't something to be proud of, so the whole thing didn't actually bother me much (you can't race a F1 in a minicar with 60hp :)).

So, I've been using Unity 2D since a couple weeks ago, when I decided to give this issue a "one last try" to fix. I managed to get a fully functional 3D Unity (without the lags, slowness, etc.) by changing this feature in my BIOS: **"VGA Share Memory"**. Since my graphic card is integrated on my MBO, earlier I configured it to use the max. shared memory available (256MB). When I reduced it to the minimum (32MB) the whole thing blossomed - Unity appeared to be fast and responsive. I've tried it with NVidia 173 drivers available via Ubuntu repos and with drivers that I downloaded directly from NVidia (v173.14.36), which I'm using right now, and everything looks ok ..

Now, why is this option (obviously) important and why did it bring so much performance upgrade - beats me (I can't think of any tehnically "legal" answer, hopefully someone will eventually come up with some explanation) ..

Anyway, I tought it was worth mentioning, maybe this'll be useful to someone ..

---

### Post by johnnerpb on 2014-07-08
Thanks have the same mobo and cpu thought all was lost till i read this!!

---

