---
title: "[video] Please help me, resoution/screen problem"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by fast_fxstbi on 2007-11-27
Hi all, I'm posting here cause you're maybe my last chance to make
my notebook Clevo m73 works properly with gnu/linux ubuntu 7.10 and....to avoid been
licensed from my boss cause I've nstalled it assuring it'll works...

Notebook has this specifics:
Processor: Intel Core 2 duo T7300 2.0
DDRII 1024Mb Pc667 (1x1024Mb)
Display: 12,1&#8221; W-XGA+TFT Glare /non glare Type Risoluzione Max 1280x800
Core Logic: IIntel® GM965 + ICH8M
Video controller: Intel® GM965 integrated, High preference 3D/2D graphic accelerator, Share memory architecture 256MB,Support Microsoft DirectX® 9 3D graphic accelerator


My only problem is with resolution/3d effetcs. It seems to not visualize
the 1280x800 widescreen... I've reinstalled ubuntu 7.10 and now the
progs windows are able to fill all the screen, but only if I grab'em. If
I click on "maximize" they fit only the 4/3 of the screen... in
System->Preferences->Resoution and in System->Admin->screen there's
nothin' about 1280x800 but only 1024x768... 

Last time I've installed ubuntu I had compiz work properly with all the
3d effects but... a 4/3 screen alway without been able to "expand" the
windows...  

Instead now I'm able to expand windows but.... it seems to don't
recognize the 3d card in fact I'm not able to turn on the visual effects
under System->Preferences->Aspect->Visual Effetcs  (Desktop effects
could not be enabled) so Compiz & C. doesn't works...


ATTACHED: actual defaut xorg,conf , screenshot with 3d graphic ok (but 4/3 screen), screenshot now (16/9...more or less...I have to enlarge windows manually to fit all the screen...and no visual 3d effects workin')

Could anyone help me please??

Thanks very much.

My best regards

Andrea

---

### Post by fast_fxstbi on 2007-11-27
sorry it's a Clevo M72 R (italian name nev@da-ax) known also as Sager 7260, Pro-Star 7220

---

### Post by fast_fxstbi on 2007-11-28
noone could help me... please?

---

### Post by dnice6363 on 2007-11-28
I was having alot of issues with Compiz myself.  It seems like the program does not run over 1024x768.  I had to make some changes to the config in xorg and another director.  I also had to change the depth to 16 instead of 24.  I would try to change the xorg config to have a screen size of 1024x768 at a depth of 16 to see if the display works properly.

---

### Post by qamelian on 2007-11-28
> **fast_fxstbi said:**
> noone could help me... please?

Check out the link below. The OP in that thread seems like he might have a solution to your problem.

[http://ubuntuforums.org/showthread.php?t=506744&highlight=GM965](http://ubuntuforums.org/showthread.php?t=506744&highlight=GM965)

---

