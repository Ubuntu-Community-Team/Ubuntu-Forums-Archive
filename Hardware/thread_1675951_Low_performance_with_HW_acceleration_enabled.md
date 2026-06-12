---
title: "Low performance with HW acceleration enabled"
date: 2011-01-26
forum: Hardware
---

### Post by Bucic on 2011-01-26
Even with all special effects my Gnome environment still works sluggish.  Inkscape is unusable (with some additional refreshing issue on the  rulers) and when I try to draw something in GIMP the line/spray etc.  moves at 2 inches (5 cm) per second. CPU usage is almost constantly over  80%, RAM usage at 300 of 600 MB. I know it's just an old laptop but it works FAR worse than my girlfriend's Asus Eee 1005 netbook running Windows 7 starter!

AMD Turion64 1.6 GHz
~600 MB RAM


```
glxgears
```gives 60 FPS

```
glxinfo |grep rendering
direct rendering: Yes

```

```
gksudo gedit /etc/X11/xorg.conf

```The file is blank! :shock:


```
lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

```No graphics drivers are listed under Additional Drivers

---

### Post by Bucic on 2011-01-27
Anyone?

---

### Post by mastablasta on 2011-01-27
opensource drivers for Xpress200 seem to be causing some problems. the only solution is to try and to install testing verson (i think it's testing) of opensource xorg drivers. or to wait until they solve the issues.
 
apaprently it helps with xpress 300. have a look for more infor here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
basically you would be looking for: xserver-xorg-video-radeon
 
Or the bleeding egde: 
[http://ubuntuforums.org/showthread.php?t=1476691](http://ubuntuforums.org/showthread.php?t=1476691)
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Bucic on 2011-01-27
Thank you very much for your response! :) May I count on you if I post my findings/testing results? Would testing the performance (e.g. in GIMP) using a live CD be a valuable information?

One thing I tested yesterday. I enabled Extra effects in Appearance settings (GNOME) and the maximize/minimize window effect (a "boing!" gello) seems perfectly smooth and having very little impact on CPU. I don't know what to think about it.

---

### Post by cchhrriiss121212 on 2011-01-27
> Even with all special effects my Gnome environment still works sluggish.
Performance will be better if you turn all effects off, and with that machine you should consider using a lighter desktop environment. LXDE should be a bit smoother.

---

### Post by Bucic on 2011-01-27
> **cchhrriiss121212 said:**
> Performance will be better if you turn all effects off, and with that machine you should consider using a lighter desktop environment. LXDE should be a bit smoother.
That's the thing I wanted to highlight - the performance difference between EXTRA and NONE effects settings was minimal.

Also I plan to compare my current Ubuntu performance to performance on W**indows 7 Professional** installed. If the latter system will perform better it will be a clear indicator that there's something quirky about linux-my laptop combination i.e. there will be no sensible reason to stick to linux.

---

### Post by mastablasta on 2011-01-27
> **Bucic said:**
> Thank you very much for your response! :) May I count on you if I post my findings/testing results? 

 
Sorry, no. I am jsut a newb, that actually got lucky with these opensource drivers on an older ATI card.
 
> 
Would testing the performance (e.g. in GIMP) using a live CD be a valuable information?
.
no, definatelly not.
>  
Also I plan to compare my current Ubuntu performance to performance on W**indows 7 Professional** installed. If the latter system will perform better it will be a clear indicator that there's something quirky about linux-my laptop combination i.e. there will be no sensible reason to stick to linux. 

 
ATI didn't make the Linux drivers for your card (community people did), but they support the Win7. as i said there are still issues with opensoruce drivers and they are hit or miss. things are improving. you could try the very latest bleeding edge version. or drop linux for now (or even forever) and return later when the issues with these xpress chips get fixed. you are not the only one with xpress200 problem (search the forums), but some peopel solved it by using latest opensoruce drivers i believe.
 
whatever others say Gnome should run just fine on your computer specs. i know this because i run it on much lower specs ;-)

---

### Post by Bucic on 2011-01-27
[SIZE=3]**Ubuntu LiveCD provides multitude of my installed ubuntu **[/SIZE][SIZE=3]**performance**[/SIZE][SIZE=3]**! **[/SIZE]
I've just tested it using GIMP. 

On my installed Ubuntu:
GIMP unusable. Even regular brush at default scale (1.0) won't keep up with my cursor when I do som zig-zags.

On Ubuntu LiveCD:
GIMP works exactly the same as on my hi-end monster - enough said! Even airbrush at scale 10 works like a charm.

---

### Post by Bucic on 2011-01-27
Can someone help me out here? I've got few questions regarding the links **mastablasta** provided:

**0. Why the hell the LiveCD version of Ubuntu provides me with superior performance?**

1. How do I check if I don't use the latest Open Source driver already?
(maybe it's installed already...)

2. If I decide to go for xorg-edgers driver - where is a noob friendly guide. Guys who soar around those drivers seem to take everything for granted.

3. Is it normal that both of these ... are installed together? 
xserver-xorg-video-radeon
xserver-xorg-video-radeon-ati
xserver-xorg-video-mach64
xserver-xorg-video-r128

Along with drivers (?) for many other cards?


4. If everything fails - what is the latest ubuntu + driver combination that is reported to work?

---

### Post by Bucic on 2011-01-27
Bump:(

I just tried installing xorg-edgers drivers like this
> **Fafler said:**
> ```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get install ppa-purge
sudo apt-get update

```
...and restart.
I didn't notice any changes at all.

Is there anything I should know before I switch to Ubuntu 8.04 LTS?
> **Mark Phelps said:**
> For future reference, the last ATI fglrx  drivers that DID support your card came with Catalyst version 9.3 -- and  that worked with Ubuntu versions prior to 9.04.

ATI has said several times that they will NOT be releasing new Lnix  drivers for those cards.  So, there's no point in trying out any new  driver versions.

---

### Post by mastablasta on 2011-01-28
> **Bucic said:**
> Can someone help me out here? I've got few questions regarding the links **mastablasta** provided:
 
**0. Why the hell the LiveCD version of Ubuntu provides me with superior performance?**

Hmminteresting. It means drivers are ok but upon install card or x.org is configured wrongly. or the xconf or whatever the file is scalled is configured differently on liveCD. there must a a soluton to fix it on install then. sorry i can't help with the graphics card. i can only say i had a similar thing happened with sound. worked great on live but didn't work upon install.
>  
2. If I decide to go for xorg-edgers driver - where is a noob friendly guide. Guys who soar around those drivers seem to take everything for granted.
 
You already ofund how to install them... :-)
 
> 
3. Is it normal that both of these ... are installed together? 
xserver-xorg-video-radeon
xserver-xorg-video-radeon-ati
xserver-xorg-video-mach64
xserver-xorg-video-r128
 
Along with drivers (?) for many other cards?
 
 
Yes this is normal as drivers (the open source ones) are part of the Linux Kernel. Linux works diffrently than windows.
 > 
4. If everything fails - what is the latest ubuntu + driver combination that is reported to work?
 Better would be combination of hardware + existing drivers. some not so late ATi (or now they are called AMD) cards have proprietary drivers that work well. also most Nvidia cards work well as nVidia is collaborating a lot with community. AMD basically just started to include them...
 
have you tried already adding nomodeset to kernel boot parameters? :
[http://ubuntuforums.org/showthread.php?t=1475045&page=4](http://ubuntuforums.org/showthread.php?t=1475045&page=4)
 
The live Cd maybe botos with this set to off. i see you already replied in another thread on this, but i wonder did you try it? does it help?

---

### Post by Bucic on 2011-01-28
> **mastablasta said:**
> Hmminteresting. It means drivers are ok but upon install card or x.org is configured wrongly. or the xconf or whatever the file is scalled is configured differently on liveCD. there must a a soluton to fix it on install then.
Yes, I think so too. It would be an overkill to switch back to 8.04 when 10.10 LiveCD works perfectly! Also it's almost certain that I will stumble upon yet another problem like this one in 8.04. Vicious wheel that is...



[CENTER]**What worries me is that I'm close and it's average users like you who are more willing to help than savvys...**
Or is the forum less active than I initially thought?[/CENTER]



> **mastablasta said:**
> 
You already fund how to install them... :-)
Yup, already found answers to questions 2 and 4 from my post #9.
 
 > **mastablasta said:**
> 
Yes this is normal as drivers (the open source ones) are part of the Linux Kernel. Linux works diffrently than windows.
OK, thanks.
 
> **mastablasta said:**
> 
 Better would be combination of hardware + existing drivers. some not so late ATi (or now they are called AMD) cards have proprietary drivers that work well.
It's not an option. Low-end, old hardware was THE reason why I evaluated installing Linux as justified.

 > **mastablasta said:**
> 
have you tried already adding nomodeset to kernel boot parameters? :
[http://ubuntuforums.org/showthread.php?t=1475045&page=4](http://ubuntuforums.org/showthread.php?t=1475045&page=4)
The live Cd maybe botos with this set to off. i see you already replied in another thread on this, but i wonder did you try it? does it help?
Yes, I have. I'll have to confirm that I did it properly though and I'll report back after that and the trial with xorg.conf copied from LiveCD.


One more thing - **glxgears without vsync** (without vertical synchronization):
Do you know how to achieve this? Currently they will always show 60 FPS for me which makes it useless. Some say that glxdrivers are not for benchmarking. Well, they are more than enough to be used as an indicator if something works or not, which is exactly my case. I couldn't find anything using search engines.

---

### Post by Bucic on 2011-01-28
An additional quick question - **nomodeset** disables automatic configuration of the graphics by KSM. In that case should xorg.conf contents be generated after **nomodeset** has been successfully forced?

---

### Post by Bucic on 2011-01-29
I checked it today - there is no xorg.conf file in my LiveCD's filesystem. What's interesting the file is missing also from my installed Ubuntu filesystem :shock:


Now I can draw in GIMP without any lag. That's not all. I painted a 1600x1200 image with airbrush a bit, made it windowed, enabled Extra Effects for desktop and did constant window shaking for 30 seconds so that the windows was wobbling and deforming. The CPU utilization settled on merely 45 % !  At idle (nothing done on desktop) CPU ut. settles at ~22 %.

What I did?
I don't recall doing anything but:
```
sudo gedit /etc/default/grub
```

Line
*GRUB_CMDLINE_LINUX="quiet splash"* commented out (*# GRUB_CMDLINE_LINUX="quiet splash"*)

Added line 
*GRUB_CMDLINE_LINUX="nomodeset"*

File saved.

```
sudo update grub
```

Computer restart.

---

### Post by cascade9 on 2011-01-31
/etc/X11/xorg.conf has been used less and less since 8.04. You can create an /etc/X11/xorg.conf file by booting into 'recovery' mode then running-

sudo Xorg -configure
 
Or at leas that was how to do it last time I tried, I dont know if thats been changed. 

> **Bucic said:**
> Is there anything I should know before I switch to Ubuntu 8.04 LTS?

Yes. Support for the desktop version expires in april 2011. 

> **Bucic said:**
> Also I plan to compare my current Ubuntu performance to performance on W**indows 7 Professional** installed. If the latter system will perform better it will be a clear indicator that there's something quirky about linux-my laptop combination i.e. there will be no sensible reason to stick to linux.

Ubuntu is a linux distro, but that doesnt mean that a different distro wont run a lot better on your system. 

From the problems you are having, I'd guess that its possible win7 would run better. Then again, you are so far below the requirements for win7 it might not even install.  

I'm not convinced that its a video driver problem, if it was then newer drivers should have at least helped. Bad drivers shouldnt make your system run at 80% CPU use.

---

### Post by Bucic on 2011-01-31
> **cascade9 said:**
> /etc/X11/xorg.conf has been used less and less since 8.04. You can create an /etc/X11/xorg.conf file by booting into 'recovery' mode then running-

sudo Xorg -configure
 
Or at leas that was how to do it last time I tried, I dont know if thats been changed. 
It seems that I don't need xorg.conf. Everything is blazing fast now. Maybe except glxgears that score ~500 but this concerns me less.


> **cascade9 said:**
> 
Yes. Support for the desktop version expires in april 2011. 
I don't have to move back to any version as I **luckily** tested 10.10 LiveCD working fine and fixed the installed version too. But thanks for the info. 

> **cascade9 said:**
> 
Ubuntu is a linux distro, but that doesnt mean that a different distro wont run a lot better on your system.
I'm relatively new to Ubuntu but I know two things already:
- edit: driver problems are common **for all distros**
- switching to another distro may leave you with the same problem... and a couple of additional problems as a bonus


 
> **cascade9 said:**
> 
From the problems you are having, I'd guess that its possible win7 would run better. Then again, you are so far below the requirements for win7 it might not even install.
Before I fixed the performance issue on U 10.10 - you were actually right. Win 7 was running perfectly fine even with aero enabled. I was about to disable it though...

  
> **cascade9 said:**
> 
I'm not convinced that its a video driver problem, if it was then newer drivers should have at least helped. Bad drivers shouldnt make your system run at 80% CPU use.
See above - what I did and what effects it gave. I can't drop any additional info.

---

### Post by cascade9 on 2011-01-31
> **Bucic said:**
> I'm relatively new to Ubuntu but I know two things already:
- driver problems are common

Driver problems always exist. Even with windows. ;) Ubuntu is probably one of the worst for driver comptibility, because they tend to move to the newest version of xorg when other distros arent so agressive. 

> **Bucic said:**
> - switching to another distro may leave you with the same problem... and a couple of additional problems as a bonus

Or moving distro can fix things.

---

### Post by Bucic on 2011-01-31
> **cascade9 said:**
> Driver probably always exist. Even with windows. ;) 
Oh please :roll: Besides, I meant "common for all distros". Post edited.

> **cascade9 said:**
> 
Or moving distro can fix things.
What do you mean by *moving*?

---

### Post by cascade9 on 2011-01-31
Moving, chaning distro. 

I typo-ed myself, I meant to say "Driver problems always exist." (edited my post to avoid confusing others). 

The problems are not always common for all distros. nVidia 96.xx drivers would not work with 10.10 up till recently, due to the newer xorg version. Theres been a lot of examples of that sort of thing, thats just one of the top of my head....

---

### Post by Bucic on 2011-01-31
Anyway, regarding me having my issue somewhat fixed - I'm afraid it may be some quasirandom stuff and that I may not succeed the next time e.g. when reinstalling Ubuntu.

---

### Post by cascade9 on 2011-01-31
At least its working. ;) 

Dont worry about the seemingly quasi-random stuff. The 1st time I installed a linux distro, I made a right mess of it. Every time its got easier and easier, and now I find it much easier to install a linux distro than windows :lolflag:

---

### Post by Bucic on 2011-02-01
This was an extremely silly bug in Ubuntu and I'm planning on filling a report. The DOH! of the month.

---

