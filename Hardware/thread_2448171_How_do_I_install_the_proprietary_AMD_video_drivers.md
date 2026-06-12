---
title: "How do I install the proprietary AMD video drivers in Ubuntu 20.04"
date: 2020-08-03
forum: Hardware
---

### Post by codosaurus on 2020-08-03
What is the correct way to install proprietary AMD video drivers in Ubuntu 20.04?
I have an AMD A10-5800K APU and I am trying to install AMD Proprietary video drivers.
The 64 bit ubuntu option on AMD's driver download page (link below) has me download a driver called fglrx_15.201-0ubuntu1_amd64_UB_14.01.deb 

[https://www.amd.com/en/support/apu/amd-series-processors/amd-a10-series-apu-for-desktops/a10-5800k-radeon-hd-7660d](https://www.amd.com/en/support/apu/amd-series-processors/amd-a10-series-apu-for-desktops/a10-5800k-radeon-hd-7660d)

But the directions assume I have a downloaded a file with a tar.gz extension.
Also, I have read in other places that "fglrx" drivers are dead.

The 64 bit linux option on the (above) download page has me download a folder called "amd-catalyst-15.9-linux-installer-15.201.1151-x86.x86_64.zip".
The executable installer within complains:
ERROR: Detected X Server Version 'X server 1.20.8-64a is not supported.

So what is the correct method to install?

---

### Post by CatKiller on 2020-08-03
fglrx is most definitely dead. Why do you feel that you need to use a proprietary driver at all?

---

### Post by codosaurus on 2020-08-03
I have managed to interest my son in Linux by showing him that he can play minecraft.
Unfortunately, he has gone back to playing on the xbox because his framerate is just over 4 and it makes playing minecraft painful on his ubuntu machine.
He points out that his sister gets a framerate over 72 on her windows PC and minecarft looks great.

---

### Post by Holger_Gehrke on 2020-08-03
AMD are known to release the kind of data needed for writing a good graphics driver. So for everything except one or two of the very newest chips by AMD there is no proprietary driver and none is needed. The proprietary part is mostly needed if you want to use the GPU for non-graphical calculations (openCL, I think). Since the graphics core used on the A10-5800k - the Radeon HD7660D - had already been around for a while when the chip was introduced in 2012, the developers had more than enough time to get things working. If I'm not misreading the [feature matrix at x.org]("https://www.x.org/wiki/RadeonFeature/") that core is part of the "Northern Islands" family of chips and almost everything they can do is supported. So the problem is probably not related to the graphics driver.

Holger

Edit: Just looked in the German Ubuntu wiki, and there they basically said that Minecraft used to work well with the old proprietary driver and doesn't do well at all with the open source driver. So it seems that AMD graphics and Minecraft is a combination to be avoided.

---

### Post by Yellow Pasque on 2020-08-03
> **codosaurus said:**
> What is the correct way to install proprietary AMD video drivers in Ubuntu 20.04?

I don't know why performance on Minecraft is poor, but I can tell you that you're barking up the wrong tree with proprietary drivers:
- The current proprietary AMD drivers (a.k.a. amdgpu-pro) do not support the GPU on the A10-7800K.
- The older fglrx/Catalyst proprietary driver will not work with any modern/supported version of Ubuntu.

---

### Post by mastablasta on 2020-08-04
> **codosaurus said:**
> I have managed to interest my son in Linux by showing him that he can play minecraft.
Unfortunately, he has gone back to playing on the xbox because his framerate is just over 4 and it makes playing minecraft painful on his ubuntu machine.
He points out that his sister gets a framerate over 72 on her windows PC and minecarft looks great.

1. what Java are you using? OpenJDK or Oracle?
2. is the card being correctly detected by the OS and is GPU acceleration being used? radeon drivers should work fine.
3. is Minecraft using the openGL acceleration? 
4. are you running full screen? acceleration only used on full screen game or is something running in the background?
5. have you tried changing any video setting in minecraft?
6. that's an APU so it uses RAM from the main board and does not have a dedicated one - how much ram do you have? how much ram did you assign to java when you ran the Minecraft?

i have a much much weaker APU chip and at least version 1.5.1 ran fine on it. i haven't tried the latest ones, but that laptop has very little ram and the CPU is not powerful (quite weak in fact - benchmark 700 points as compared to modern CPU that mostly get over 8000 points). minecraft is quite heavy on CPU.

---

### Post by codosaurus on 2020-08-04
> **mastablasta said:**
> 
1. what Java are you using? OpenJDK or Oracle?


The frame rates I quoted actually come from the Phoronix test suite.  The jerkiness we see in their test mirrors what we see in minecarft.
So I guess I dont know which Java we are using. How do I find out? Why does it matter?

> **mastablasta said:**
> 
2. is the card being correctly detected by the OS and is GPU acceleration being used? radeon drivers should work fine.


It shows up correctly when I do: "[COLOR=#000000][FONT=menlo]sudo lshw -c video". Is that what you mean?
[/FONT][/COLOR]It is not that the radeon drivers don't "work", it is that they appear to work poorly. 4 FPS.

> **mastablasta said:**
> 
3. is Minecraft using the openGL acceleration? 

I don't know.  How do I check this?

> **mastablasta said:**
> 
4. are you running full screen? acceleration only used on full screen game or is something running in the background?

The Phoronix test suite reports only a slight difference in framerate between fullscreen and Windowed.

> **mastablasta said:**
> 
5. have you tried changing any video setting in minecraft?

I have not. I assume that minecraft will not outperform Phoronix. What should I try?

> **mastablasta said:**
> 
6. that's an APU so it uses RAM from the main board and does not have a dedicated one - how much ram do you have? how much ram did you assign to java when you ran the Minecraft?

That sounds like a good idea.  I will check into that.

> **mastablasta said:**
> 
i have a much much weaker APU chip and at least version 1.5.1 ran fine on it. i haven't tried the latest ones, but that laptop has very little ram and the CPU is not powerful (quite weak in fact - benchmark 700 points as compared to modern CPU that mostly get over 8000 points). minecraft is quite heavy on CPU.
I am not sure comparisons to earlier versions of minecraft are relevant.
Here is my comparison:
I have another PC with an AMD Athlon and GeForce GTX 1050ti video card. It also runs Ubuntu 20.04.
I ran the phoronix test suite benchmark test using the open source driver and got a frame rate of just over 8.
I installed the driver from nvidia
The Phoronix benchmarg showed a frame rate of around 78.
This is the experience I am trying to duplicate.

So are you saying that there is no other driver for my APU that works in ubuntu 20.04?

---

### Post by Yellow Pasque on 2020-08-04
>  have another PC with an AMD Athlon and GeForce GTX 1050ti video card. It also runs Ubuntu 20.04.
I ran the phoronix test suite benchmark test using the open source driver and got a frame rate of just over 8.
I installed the driver from nvidia
The Phoronix benchmarg showed a frame rate of around 78.
This is the experience I am trying to duplicate.


The reason you saw such a big jump is because nouveau is extremely slow on newer Nvidia cards. Nouveau is stuck at minimal boot clocks (because Nvidia never released their signed firmware for nouveau to use): [https://www.phoronix.com/scan.php?page=article&item=nvidia-nouveau-2019&num=1](https://www.phoronix.com/scan.php?page=article&item=nvidia-nouveau-2019&num=1)
That is not relevant to AMD. A long time (> 10 years) ago, the AMD proprietary driver outperformed the open-source one, but the open-source driver caught up and surpassed it with support from AMD: [https://www.phoronix.com/scan.php?page=article&item=radeon-software-1820&num=1](https://www.phoronix.com/scan.php?page=article&item=radeon-software-1820&num=1)

> So are you saying that there is no other driver for my APU that works in ubuntu 20.04? 
Yes (not counting generic, unaccelerated drivers), The correct driver is installed out of the box. Check with:
```
glxinfo -B
```

---

### Post by Yellow Pasque on 2020-08-04
Also note that your GPU doesn't meet Minecraft's minimum requirements: [https://help.minecraft.net/hc/en-us/articles/360035131371-Minecraft-Java-Edition-system-requirements-](https://help.minecraft.net/hc/en-us/articles/360035131371-Minecraft-Java-Edition-system-requirements-)

---

### Post by codosaurus on 2020-08-04
> **Yellow Pasque said:**
> Also note that your GPU doesn't meet Minecraft's minimum requirements: [https://help.minecraft.net/hc/en-us/articles/360035131371-Minecraft-Java-Edition-system-requirements-](https://help.minecraft.net/hc/en-us/articles/360035131371-Minecraft-Java-Edition-system-requirements-)

Interesting point, but how so?
Your link lists minimum CPU as an A8, I have an A10-5800K.
It lists minimum GPU as Radeon HD 7000 series.
The A10-5800K has an HD7660D.

---

### Post by Yellow Pasque on 2020-08-04
NVM, Duplicate post

---

### Post by Yellow Pasque on 2020-08-04
> **codosaurus said:**
> It lists minimum GPU as Radeon HD 7000 series. The A10-5800K has an HD7660D.

Read it again. That is for higher-powered discrete cards. It's suggesting Kaveri (A#-7000 series) for integrated graphics.
GPU (**Integrated**): AMD Radeon R5 series (Kaveri line) with OpenGL 4.4

[https://en.wikipedia.org/wiki/List_of_AMD_accelerated_processing_units#%22Kaveri%22_(2014)]("https://en.wikipedia.org/wiki/List_of_AMD_accelerated_processing_units#%22Kaveri%22_(2014)")

---

### Post by mastablasta on 2020-08-05
this is the actual GPu chip right?: AMD Radeon HD 7660D (800 MHz)

it's not some super GPu chip, but it should run minecraft

> **codosaurus said:**
> The frame rates I quoted actually come from the Phoronix test suite.  The jerkiness we see in their test mirrors what we see in minecarft.
So I guess I dont know which Java we are using. How do I find out? Why does it matter?


```
java -version
```

it shouldn't matter but sometimes it does with minecraft.

> 
It shows up correctly when I do: "[COLOR=#000000][FONT=menlo]sudo lshw -c video". Is that what you mean?
[/FONT][/COLOR]It is not that the radeon drivers don't "work", it is that they appear to work poorly. 4 FPS.

I don't know.  How do I check this?


you can see what is working in your video card and what is not here: [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)
there are also some switches explained one can try. done features work well.

read here on how to test hardware acceleration (under **Testing the driver**): [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

if needed you can add latest drivers using Oibaf PPA.

phoronix tests run as you set them and it depends what you are testing the chip is not something powerful to begin with so it depends what test you used and how it was tested. For example KDE will automatically turn off background acceleration when you run game or testing full screen. my tests are not impressive either. but the card can play older games reasonably well (GT 730). even Minecraft which mostly needs more CPU power than GPU to generate the area. and my CPU is 16 years old Athlon 64 single core.

it's been a while since i dealt with radeons. i had them and they all worked fine using opensource driver (i had ATI Rage, Radeon 9200, Radeon 3650 - well to be honest Rage had only partial 3D support). the one i still use is E-450 that has Radeon HD 6320 (uses 512MB of 2 GB ram). not something powerfull but it did run Left 4 Dead well and some other older games (or games based on older engines) on lower/medium settings (OpenMW, World of Padman,Quake2...). it would run even better, if i added more ram to it, but the Win7 Starter (dual boot) can't handle more ram and on rare occasion i still need access to windows PC.

One of my kids got himself a laptop (he might need one for school during these times) and he has Vega 8 that is using AMDGPU. runs really well and i am glad they opened the drivers up to this point.

---
i would troubleshoot Minecraft like this.

1. check if hardware acceleration is working (**Testing the driver** mentioned above)

2. make sure you run the older xorg  display server and not the new Wayland (i am not sure what Ubuntu defaults to but i know you can change this on login screen) - [https://askubuntu.com/questions/904940/how-can-i-tell-if-i-am-running-wayland](https://askubuntu.com/questions/904940/how-can-i-tell-if-i-am-running-wayland)

3. check any setting that enables you to turn off GPU acceleration of windows drawing while game is running full screen. Ubuntu probably this option now as well

4. check minecraft settings - maybe you have high resolution set. set all on minimum/low then work up from there. see where the soft spot it. at least on super low the game should run if it has at least partial GPU acceleration.

5. make sure you don't assign too much ram to java for example launch it with:
```
java -Xms512M -Xmx1G -jar '/home/user/.minecraft/Launcher.jar'

```
or
```
java -Xms1G -Xmx2G -jar '/home/user/.minecraft/Launcher.jar'

```

6. try Oracle java - installing it was easy via PPA but Oracle made it more difficult now. still Linux uprising takes care of the install, you just manuly download the installation file from Oracle and put it to the /var/cache/java folder.: [https://www.linuxuprising.com/2019/06/new-oracle-java-11-installer-for-ubuntu.html](https://www.linuxuprising.com/2019/06/new-oracle-java-11-installer-for-ubuntu.html)

7. install latest drivers via Oibaf PPA, because this chip got opensource drivers quite recently, so newer might have more stuff fixed.


you could also add (try) Mate desktop or similar to reduce system resources used by the OS. other light options to try are XFCE (Xubuntu) and LXQT (Lubuntu). KDE is also not that bad if you disable "*the bling*" and effects.

---

### Post by Yellow Pasque on 2020-08-05
In addition to above suggestions, you may want to try enabling OpenGL 4.4 and see if that helps. For example:
```
MESA_GL_VERSION_OVERRIDE=4.4 MESA_GLSL_VERSION_OVERRIDE=440 java -Xms512M -Xmx1G -jar '/home/user/.minecraft/Launcher.jar'
```

Background info: [https://www.phoronix.com/scan.php?page=news_item&px=R600g-Hits-GL-4.4-Unofficially](https://www.phoronix.com/scan.php?page=news_item&px=R600g-Hits-GL-4.4-Unofficially)
soft fp64 has since been merged and optimized.

Remember the Radeon "r600" 3D driver doesn't officially claim OpenGL 4.x support and hasn't passed the tests for it, so don't be surprised if there are glitches (and don't file bugs). But you never know until you try..

---

