---
title: "First time user, very confused"
date: 2008-08-23
forum: General Help
---

### Post by woodyfly on 2008-08-23
First time using ubuntu and i gotta say.. im VERY disappointed and confused. Ive spent over 2 hours trying to SIMPLY change my desktop resolution from 640x480 to anything higher. Ive managed to get it to 1024 one time but it reverted back after a reboot. Im stuck reading the forums with 640x480 @ 50hz and this is killing my eyes and brain. Even when i did manage to get 1024, the refresh rate was capped at 85 (i can go up to 100 with 1024). By searching around the forums, apparently its not just me.

 I installed my nvidia drivers thru "hardware drivers" and when i go to edit my xorg.conf ... theres no variables or numbers... just the default headers

---

### Post by LateNiteTV on 2008-08-23
post your xorg.conf file here.

---

### Post by zenthanian on 2008-08-23
I have done several installs on several machines and had zero problems.  

Can you post the type/model of the video card.  Also, do you have another video card to try?

(Please excuse a perhaps obvious question -- are you running Ubuntu from a live CD?  If so everything is running in memory and will be removed when you reboot.)

---

### Post by youthforlinux on 2008-08-23
try installing nvidia-settings and using that...its a gui

if it is not installed go to the terminal and paste:

```
sudo aptitude install nvidia-settings
```

yeah and there's a chance your nvidia drivers aren't installed properly as aaid before give some details of this video card....

---

### Post by pfdevil on 2008-08-23
Yeah this really sucks, I'd recommend first to uninstall the nvidia restricted drivers, and let mesa take over for a while. Uninstall the drivers reboot, select ubuntu recovery select xfix if present and load ubuntu. Post if things is back to normal and then we will start installing your nvidia drivers via envy.

---

### Post by silkstone on 2008-08-23
Also, what video card are you using?

Please don't get frustrated too soon! Installing Windows from scratch can actually be a lot more difficult.

P.S. Many LCD screens do not use refresh rates over 60Hz. You should check your monitor spec. Using too high a value may cause damage.

---

### Post by woodyfly on 2008-08-23
JUST when i thought this cannot get possibly worse, i now cannot even load ubuntu. I get a busybox black screen... apparently my xorg is messed up, says my friend..

BTW. I used wubi to install a dual boot from my windows xp

Im using a 7600 gs and in the nvidia-settings, the max goes up to only 640x480 as well.

---

### Post by pfdevil on 2008-08-23
Just reset the xorg service.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by upchucky on 2008-08-23
envy is a work around for nvidia installs, this is the right way to do a nvidia card, it solves the wrong resolution problems everyone has.



[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

---

### Post by woodyfly on 2008-08-23
> **pfdevil said:**
> Just reset the xorg service.

```
sudo dpkg-reconfigure xserver-xorg
```

I cant do that, i cannot even load ubuntu or get a prompt. Im doing a clean reinstall. God, why do i have to download this 700mb installation thing for ubuntu again. I have a buddy on mirc trying to help, he says to use envyNG to install nvidia. Right now, im about to cut my throat. Ive been starin at a 50refresh rate screen for hours, my head is about to fall off. How is a beginner to linux/ubuntu supposed to know all these things?

---

### Post by pfdevil on 2008-08-23
You do not have to reinstall, load ubuntu recovery and select root prompt then type it.

---

### Post by upchucky on 2008-08-23
you do not have to reinstall, this is not windows, your xorg has got wrong info in it, just need to edit it at the command line to get it working again, what you have is the busybox when it is trying to boot up.

you gotta read about busybox, and how to boot to command line and how to set up xorg file, the cd you used to install will let you edit the xorg file to fix it.

---

### Post by youthforlinux on 2008-08-23
HOLD ON

you are using wubi which is dependent on your windows hard drive partition, which is corrupted....which means you can't boot into ubuntu, this is the reason that if you can do a full install later go for it....to fix this boot  into windows, and in My Computer right click your hard drive, go to Tools and such and go to scandisk, make sure automatically fix errors is checked, it will prompt to say that restart is required, then restart and boot to windows to do disk check and then reboot into buntu, to prevent this do not turn of windows without properly shutting down otheriwse the same problem occur, you must check the disk before we can proceed helping you with this video card problem!!!!

---

### Post by woodyfly on 2008-08-23
I forgot to say guys, i didnt use a cd. I used wubi from windows to install a dual boot

---

### Post by Sinkingships7 on 2008-08-23
A refresh rate of 50 should be absolutely fine. I'm running a 20' LCD monitor at 1680x1050 with a refresh rate of 51 Hz, and the picture is clear and crisp.

---

### Post by pfdevil on 2008-08-23
> **woodyfly said:**
> I forgot to say guys, i didnt use a cd. I used wubi from windows to install a dual boot

Hey don't worry. I mounted an kubuntu ISO through daemon tools in Windows and installed it with wubi and everything went great.

---

### Post by Too Late on 2008-08-23
> **woodyfly said:**
> How is a beginner to linux/ubuntu supposed to know all these things?
Unfortunately, Ubuntu (nor many other Linux distros) is not designed for CRT users (edit: as you can see from the posts above... everyone is assuming that you have a LCD). I've used buntus for some three years now, and every single installation have had issues with resolution, refresh rates and so on. In addition, it's easy to see that the designers of these desktop environments don't use vertical resolution lower than 1024 pixels. However, all the problems can be resolved.

---

### Post by upchucky on 2008-08-23
if you can still boot windows, download ubuntu, make a iso cd to do an install, reinstall with the cd as a dual boot.

if windows will not boot either then you need advanced supergrub to fix the masterbootloader.

you can fix the xorg file with the ubuntu iso cd you made, gonna probably have to do this to get vid driver working later anyway.

---

### Post by youthforlinux on 2008-08-23
> **Too Late said:**
> Unfortunately, Ubuntu (nor many other Linux distros) is not designed for CRT users (edit: as you can see from the posts above... everyone is assuming that you have a LCD). I've used buntus for some three years now, and every single installation have had issues with resolution, refresh rates and so on. In addition, it's easy to see that the designers of these desktop environments don't use vertical resolution lower than 1024 pixels. However, all the problems can be resolved.


Well, I had ubuntu hardy on two CRTs and it worked great, now only on one CRT(yay upgraded to LCD this year, finally!)....but i've had no problems with the screen resolution, but of course your results may vary, but if you're not confident enough to dual-boot, wubi will still work, you just need to fix that windows partition with scandisk as I stated above, then specify video card....:lolflag::lolflag:

---

### Post by woodyfly on 2008-08-23
> **Sinkingships7 said:**
> A refresh rate of 50 should be absolutely fine. I'm running a 20' LCD monitor at 1680x1050 with a refresh rate of 51 Hz, and the picture is clear and crisp.

Maybe for lcd is fine but crt , thats a JOKE. Just finished reinstalling and im back on ubuntu now. I installed envyNG and the max is still 640x480.. whats next? lol

Heres the xorg.conf (which took me about 30 minutes of searching to even find out how to run it)

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by youthforlinux on 2008-08-23
try installing the nvidia-settings package and tweaking that stuff from there?

---

### Post by pfdevil on 2008-08-23
Hey did you install the nvidia drivers via Envy-NG

---

### Post by Sinkingships7 on 2008-08-23
> **woodyfly said:**
> Maybe for lcd is fine but crt , thats a JOKE. Just finished reinstalling and im back on ubuntu now. I installed envyNG and the max is still 640x480.. whats next? lol



Oops, assumed you had an LCD. ^_^

---

### Post by woodyfly on 2008-08-23
> **pfdevil said:**
> Hey did you install the nvidia drivers via Envy-NG

Yes

---

### Post by youthforlinux on 2008-08-23
maybe try ```
gksu diplayconfig-gtk
``` tho nvdia-settings has worked better for me in the past

---

### Post by gjoellee on 2008-08-23
I will make it easy for you:
[http://kshoster.net/?c=tipsandtricks&h=xfix](http://kshoster.net/?c=tipsandtricks&h=xfix)

---

### Post by woodyfly on 2008-08-23
> **gjoellee said:**
> I will make it easy for you:
[http://kshoster.net/?c=tipsandtricks&h=xfix](http://kshoster.net/?c=tipsandtricks&h=xfix)

And this one liner command is supposed to fix my video card problem?

---

### Post by mb_webguy on 2008-08-23
> **woodyfly said:**
> And this one liner command is supposed to fix my video card problem?

Um, I think it's supposed to be a joke, but if so, it's not a very good one.  The command "sudo shutdown now" won't do any of the things mentioned in the description on that page.  All it will do is shutdown your system...

---

### Post by woodyfly on 2008-08-23
> **mb_webguy said:**
> Um, I think it's supposed to be a joke, but if so, it's not a very good one.  The command "sudo shutdown now" won't do any of the things mentioned in the description on that page.  All it will do is shutdown your system...

So in other words, he's telling me to **** ubuntu. Someone told me to do a live cd install rather than wubi..

It could be that my comp just sucks... as a matter of fact, its the reason why i wanted to switch to ubuntu

---

### Post by youthforlinux on 2008-08-24
I still think u should try nvidia-settings or displayconfig-gtk...i have had res problems with my nvidia card and these helped to fix my resolution nicely....a wubi install is a regular install just without repartitioning your windows drive....it is meant for people wanting to try out Ubuntu without having to go through the process of resizing and creating new partitions....otherwise it is the same installation, so if your card won't work in Wubi properly, it won't work witht he regular install...the only thing with the regular install is that you will see a preformance increase due to the face that it is not a loop mounted partition.

---

### Post by woodyfly on 2008-08-24
Thanks for the help everyone, but it seems nothing works. I still think one of my hardware has problems and i was planning on replacing a few things. If it had to be hardware causing this? Most likely which would be the culprit? (I have a weird problem on windows. I can run at 100refresh rate but the games still feel like theyre being played at 60 refresh rate, being very hard to shoot or concentrate. Its as if windows is forcing it to refresh at 100 but the game itself is still playing at 60refresh rate...). I dont think its my video card, ive tried another one and its the same. Would you say its a bad mobo? or processor?

---

### Post by Butthead on 2008-08-24
I didn't read this whole thread, but any changes you make to monitor settings (i.e. - resolution) has to be under root privileges or they won't stick.

Did you set the desired resolution you wanted to achieve under the "System Settings -Monitor & Display" sub-menu?

If using KDE Desktop, did you start Envy by typing "KDESUDO Envy" in the Run Command under K (KDE) Main menu and then giving it your password? :confused: 

Don't worry, this will all get easier to understand the more you use it. :guitar:

---

