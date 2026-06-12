---
title: "Establishing 3D Acceleration for an Intel 945 graphics card in ubuntu 7.10 Guttsy"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by Jafil21 on 2007-10-26
Hello guys. I have an Intel 945 graphics card and I'm having some problems stemming from the fact that I haven't set up its 3D acceleration. I know this because of my meddling with Compiz Fusion... I used to run openSUSE, which allowed me to enable 3d acceleration upon installation and Compiz would run perfectly. Now I log into XGL sessions and the GUI lags. Firefox pages scroll down slowly, windows drag even slower, ew. Just ew.

I read [this](http://ubuntuforums.org/showthread.php?t=577141&page=2) thread but can't say the responses were quite what i am looking for.

Any help? =(

---

### Post by MaximusTG on 2007-10-26
Hmm, that's strange, I think it has to do with the fact that you use XGL, but with the intel 945 you should use AIGLX, which, according to man xorg.conf in Gutsy is enabled by default. 
I think you should just do a dpkg-reconfigure xserver-xorg (backup xorg.conf beforehand). I have the same card, and it worked out of the box. The card should use the "intel" driver,

---

### Post by Jafil21 on 2007-10-26
I went through the whole configuration, and the system is still laggy. =/

---

### Post by Jafil21 on 2007-10-27
I'm bumping this. =/

---

### Post by SteFaNweI on 2007-10-27
did you uninstall the xgl packages? as of gutsy, ubuntu _will_ use xgl if it is installed

good luck.

---

### Post by lvronghai1 on 2007-10-27
HI,

I have intel945 video cards working great with ubuntu 7.10 by using aiglx now. After fresh install,  I got somehow ok resolution, but resolution does not show at all from Preference->screen resolution. Intel driver in xorg.conf does not work for me, I have to change it to i810, after that it works great.

---

### Post by Jafil21 on 2007-10-27
> **SteFaNweI said:**
> did you uninstall the xgl packages? as of gutsy, ubuntu _will_ use xgl if it is installed

good luck.

In order to disable XGL, I made a file named disable and saved it in the ~/.config/xserver-xgl directory as instructed [here](http://ubuntuforums.org/showpost.php?p=3416144&postcount=15). However, the system is still somewhat laggy. Not as bad as previously, but still not what it was after fresh installation.

> **lvronghai1 said:**
> HI,

I have intel945 video cards working great with ubuntu 7.10 by using aiglx now. After fresh install,  I got somehow ok resolution, but resolution does not show at all from Preference->screen resolution. Intel driver in xorg.conf does not work for me, I have to change it to i810, after that it works great.

I did this, and the only thing it did was just lower my resolution from 1280 to 1024.

---

### Post by Jafil21 on 2007-10-29
Come on guys. Don't let this love child of mine die.=/

---

### Post by Jay_Rock on 2007-11-01
I got the same issue here. 
I didn't have this issue with 7.04, I may have to go back to it...damn. 
Help.

---

