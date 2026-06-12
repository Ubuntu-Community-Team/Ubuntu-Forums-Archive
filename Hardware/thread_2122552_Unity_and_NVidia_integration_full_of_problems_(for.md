---
title: "Unity and NVidia: integration full of problems (for such a long time)"
date: 2013-03-05
forum: Hardware
---

### Post by wribeiro on 2013-03-05
Since User Interface in Ubuntu was changed to Unity, in 2011, my problems with video driver began. From that time it has been difficult to use the Canonical's operating system in my work computer.
I might be wrong, but it seems that there is no determination of the development team in creating a robust driver software.
The U.I. Unity is good, really good, but it's integration with NVidia driver is a complete disaster.

Nouveau driver (open source) seems to have been abandoned and the proprietary drivers have serious problems that are never solved. Year after year, version after version.
Starting from installation, the boot via pen drive presents a screen flickering, corrupted, where the image appears blurred and cut vertically. The installation process must be run this way, unable to read information on the screen, until we can set a resolution that the image is stable and readable. An adventure!
Once you get the driver change, other problems start to happen, making it impossible to use Ubuntu.
The issues are more frequent with LibreOffice, but sometimes occur in Chromium, pgAdmin and others.

Problems with NVidia Video Driver in Ubuntu 12.10 are so serious that I was forced to install the 13.04 alpha, but there was no significant improvement.

Finally I need to know if there is any chance of this serious problem be solved and whether there will be a video driver NVidia that does not cause so many errors.

HP Pavilion dv6000
GeForce 7150M / nForce 630M/integrated/SSE2/3DNOW

---

### Post by oldfred on 2013-03-05
It is not Unity, but nVidia. And the integration of video into the kernal. With my nVidia I have had to use nomodeset until I install the nVidia proprietary drivers. And with 12.10 I also had to add kernel headers first.

But your 630m is Optimus. Linux had one of his huge rants on nVidia and a lack of support for Optimus. So they came out with this, but we have not seen anything.
       NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

But most find bumblebee works.
      
 Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
[http://ubuntuforums.org/showthread.php?t=2121707&p=12540889#post12540889](http://ubuntuforums.org/showthread.php?t=2121707&p=12540889#post12540889)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)

---

### Post by wribeiro on 2013-03-05
All these bugs affect me for years (all of them related to nvidia driver):

- [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492)
- [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1144232](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1144232)
- [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445)
- [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1085124](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1085124)
- [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/538275](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/538275)
- [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/575092](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/575092)

---

### Post by JLeon85 on 2013-03-05
Have you tried some of the other desktop environments? I've had a lot of trouble with my Nvidia card on Ubuntu, but it works flawlessly on Lubuntu.

---

### Post by wribeiro on 2013-03-05
> **JLeon85 said:**
> Have you tried some of the other desktop environments? I've had a lot of trouble with my Nvidia card on Ubuntu, but it works flawlessly on Lubuntu.
LXDE is a very good environment, but lack important tools such as battery level indicator, dual screen and other things.

---

### Post by wribeiro on 2013-03-06
I can understand that there is nothing to do on proprietary drivers.
But for me Nouveau stopped working since 2011!!! The open source community should be worried about this.

For specialized users it is not too much complicated change screen resolution under a heavy flicker and then install another video driver.
But for standard users, it can mean a definitive rejection of Ubuntu, which can also affect Canonical's plans for mobile, tablet and TV.

I think we're talking about the weakness of Ubuntu platform and it deserves greater attention.

---

### Post by wribeiro on 2013-03-17
oldfred, thank you very much for trying to help.

I installed Bumblebee, it works, but the performance is very poor and screen resolution is set wrongly.
It seems that nVidia is not worried about Linux and only provide support for Windows and Mac.
Terrible mistake!

The solution I found is install XUbuntu in a partition and forget Unity, at least until the bug be solved.
Thank you!

---

