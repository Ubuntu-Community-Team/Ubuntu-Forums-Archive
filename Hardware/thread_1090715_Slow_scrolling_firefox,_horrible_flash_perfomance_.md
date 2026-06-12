---
title: "Slow scrolling firefox, horrible flash perfomance - ati driver to blame?"
date: 2009-03-08
forum: Hardware
---

### Post by Cenoforums on 2009-03-08
Hi,

I have an ATI Mobility Radeon 9700 and things are not looking great. I've been wrestling with these performance issues for weeks now and I finally gave up. I need some help with this.

A minor background. I was running an old and quite destroyed Ubuntu 8.04 installation. The overall performance of the system was terrible, but after being on the pc for 2 or 3 hours something would happen and the performance would boost from outta nowhere. I checked the logs but I couldn't find out what was happening. I was using some version of fglrx.

My point with this is I've seen my laptop giving extremely snappy performance on all fronts while running compiz fusion. I saw it with my own eyes, I couldn't clog the cpu no matter how much i hammered the scroll wheel in firefox, flash working great etc, etc.

I thought that the problem was the 8.04 installation, so I got the new 8.10 and thought that would be the end of my problems. Nothing further from the truth.

The problems:
-Scrolling on firefox is horribly slow. Compiz or no compiz, smooth scrolling or not, firefox 3 or 2, it's just terrible. My test for this is on a google search result page. I scroll it up and down really fast and cpu goes straight to 100%, processes eating are naturally xorg and firefox itself.

-Flash video in youtube works. It shoots to 100% as well, but my CPU is fast enough and handles it. But a daily show episode is impossible to watch. teste [here]("http://www.thedailyshow.com/full-episodes/index.jhtml?episodeId=220250"). Naturally any page with a video ad drags firefox scrolling to an absurd slowness.

A friend of mine has a Nvidia card and he has none of the problems I have. So the problem is neither flash 10 nor firefox, it must be the driver. Right now I have 3 different installs testing a bunch of different things, but all of them share the same shitty performance I've been describing. 

-Ubuntu Studio 8.10 running the latest radeon driver. I tried to tweak the xorg.conf file with EXA and XAA as recommended [here]("http://forum.compiz-fusion.org/showthread.php?t=9256&highlight=firefox+slow+scrolling") but saw no difference in performance. glxgears gives ~1300fps.
-Ubuntu 8.10 running the 9.2beta catalyst driver. I haven't tried the final release yet, but honestly I don't think it's gonna matter much. Tried to tweak it as recommended [here]("http://forum.compiz-fusion.org/showthread.php?t=6794") but again, saw no difference in performance. glxgears gives ~2500fps
-Ubuntu 8.04.1 running whatever fglrx version comes preloaded. I don't know how to check the version. glxgears gives ~3000fps.

I've run out of ideas. Isn't there anyway I could tackle this? A series of verifications I could make to find out what the hell is affecting the performance? How can I find out the fglrx version contained in xorg-driver-fglrx package?

Any recommendation, insight, suggestion would be awesome. I'm running windows now because everything is so snappy, but I would really prefer to continue to use Ubuntu.

---

### Post by LordMarshall on 2009-03-11
I have the same problem on 9.04 (and had the same problem on 8.10) using an ATI Radeon Mobility M6 LY with the radeon driver. It worked fine on Arch-Linux, so I know the card is good enough handle this stuff.

---

### Post by Cenoforums on 2009-03-11
I have been thinking of trying out another disto... I'd like to keep it debian though, I know that fedora and opensuse good but I'm already familiar with aptitude for package managment.

Ease of installation would be good. Any recommendations? Do you think something like linux mint, which is based on ubuntu, would make a difference?

---

### Post by LordMarshall on 2009-03-12
I figured out a way to make at least scrolling smoother. Flash works better, but is still not ideal.

I added the following part to my xorg.conf in /etc/X11/


```
Section "Device"
	Identifier  "Configured Device"         # The name here should be the one used in the "Screen" Section below
        Driver      "ati"
        BusID       "PCI:1:0:0"
	Option          "AccelMethod"   	"XAA"
	Option          "EnablePageFlip"	"true"
	Option          "TripleBuffer"  	"true"
        Option          "AGPMode"		"4"
	Option		"DRI"			"true"
EndSection

```

Especially the option "AGPMode" may help. I'm not sure which mode your card uses.

Maybe you try that out, just make sure you make a backup of your xorg.conf and know how to restore it - if required - from console.

Changing to an Ubuntu-based distro won't change much I guess. Maybe you should have a look at debian itself.

---

### Post by Ascenti0n on 2009-03-12
First off, smooth scrolling is an option in FF that can be turned off, which in my optinion makes scrolling faster and easier:
Tools>edit>preferences>advanced

There is an option to turn off auto scrillong and smooth scrolling, uncheck smooth scrooling.

---

### Post by LordMarshall on 2009-03-12
> **Ascenti0n said:**
> First off, smooth scrolling is an option in FF that can be turned off, which in my optinion makes scrolling faster and easier:
Tools>edit>preferences>advanced

There is an option to turn off auto scrillong and smooth scrolling, uncheck smooth scrooling.

Ah I guess I've choosen the wrong words on my previous post. I never changed that option and it is turned off as I checked now. The problem was, that everything changing large parts of the visible screen was slow, resizing / moving windows, watching flash vids, and scrolling, espacially in firefox. But for me it's solved.

---

### Post by Cenoforums on 2009-03-15
LordhMarshall, that's interesting. Which graphics card do you have? what driver are you using?

I'm sure to test it on all my configs. Will Report.

---

### Post by LordMarshall on 2009-03-16
I'm using an ATI Radeon Mobility M6 LY with the radeon driver. Confing can be found in my last post.

---

### Post by Cenoforums on 2009-03-16
Alright, another thing. Can you run compiz fusion with it?

[http://forum.compiz-fusion.org/showthread.php?t=10662](http://forum.compiz-fusion.org/showthread.php?t=10662) this guy says he has to put agp mode to 1.

---

### Post by LordMarshall on 2009-03-18
First: sorry for answering late.

Well, when I run compiz all window-decoration disappears and input via keyboard is strange. Mouse works fine. Keyboard input in a terminal seems to work, but is not displayed. Using alt-f1 to open the gnome menu doesn't work. The system is not frozen, but X is useless. Switching to a console and restarting gdm solves the problem. But this depends not on wether agp mode is set to 1 or to 4, it happens both times.

I forgot to mention that I'm running Ubuntu 9.04.

---

### Post by Cenoforums on 2009-03-18
lol np.

In the meantime i tested it for myself. Honestly, I cannot say for sure if the performance is affected. It might be a bit faster, but it's still horrible.

I tested the agp mode 4 in the radeon driver. I wonder if I can do it in fglrx?

---

### Post by LordMarshall on 2009-03-19
Actually I don't think my card is supported by the fglrx driver, since it's pretty old.

---

### Post by cliffordmt on 2009-05-01
Just want to add to this thread about my experience...

I recently upgraded to 9.04 and, as soon as I did, Firefox became almost unusable.  The root of the problem was the ati driver settings, just as described in this thread.  I'm using a Dell Latitude D600 laptop with the ATI Mobility Radeon 9000 graphics card.

It turns out that as of version 9.04, the ati driver now has a different default for the acceleration setting.  Reverting to the old default setting solved the problem for me.  Here are my steps if interested:

Opened the X Window system's configuration file:
```
sudo gedit /etc/X11/xorg.conf
```Added the following in the [FONT=Courier New]Section "Device"[/FONT]:
```
Option        "AccelMethod" "XAA"
```Saved the file are restarted the system.  Firefox performs beautifully now!

---

### Post by Cenoforums on 2009-05-02
thx for the input, I'm now testing 9.04 and again the same thing has happened. All of a sudden, my performance has exploded thru the roof althought it was terribly slow for the last 3hours.

I'll try the XAA setting to see if anything is affected.

Oh, almost forgot. Are you using compiz fusion?

---

### Post by cliffordmt on 2009-05-04
No, I'm not using compiz fusion.  I have always had my Appearance > Visual Effects settings set to None.

---

### Post by jleoni on 2009-05-08
> **cliffordmt said:**
> Just want to add to this thread about my experience...

I recently upgraded to 9.04 and, as soon as I did, Firefox became almost unusable.  The root of the problem was the ati driver settings, just as described in this thread.  I'm using a Dell Latitude D600 laptop with the ATI Mobility Radeon 9000 graphics card.

It turns out that as of version 9.04, the ati driver now has a different default for the acceleration setting.  Reverting to the old default setting solved the problem for me.  Here are my steps if interested:

Opened the X Window system's configuration file:
```
sudo gedit /etc/X11/xorg.conf
```Added the following in the [FONT=Courier New]Section "Device"[/FONT]:
```
Option        "AccelMethod" "XAA"
```Saved the file are restarted the system.  Firefox performs beautifully now!

Tried this on my craptop and it seemed to help performance a great deal -- WONDERFUL snippet.

---

### Post by greenfrognet on 2009-05-09
with a Ati 1650 pro this solutions works around 80 or 90 percent, so the flash videos still watching a little slowly but firefox encrase the performance so much.

thanks

---

### Post by i_can_fly on 2009-06-23
hi all,

on my thinkpad t41(mobile radeon 9000), adding "AccelMethod" "XAA" to xorg.conf improved dramatically firefox/flash performance(to a point that it is actually faster than my new laptop which has intel video)

so, 10x a lot :)

---

### Post by Soloron on 2009-06-29
> **cliffordmt said:**
> Just want to add to this thread about my experience...

I recently upgraded to 9.04 and, as soon as I did, Firefox became almost unusable.  The root of the problem was the ati driver settings, just as described in this thread.  I'm using a Dell Latitude D600 laptop with the ATI Mobility Radeon 9000 graphics card.

It turns out that as of version 9.04, the ati driver now has a different default for the acceleration setting.  Reverting to the old default setting solved the problem for me.  Here are my steps if interested:

Opened the X Window system's configuration file:
```
sudo gedit /etc/X11/xorg.conf
```Added the following in the [FONT=Courier New]Section &quot;Device&quot;[/FONT]:
```
Option        &quot;AccelMethod&quot; &quot;XAA&quot;
```Saved the file are restarted the system.  Firefox performs beautifully now!

This solution also worked for me.

Also using a Dell Latitude D600 with 9.04.

---

### Post by Soloron on 2009-06-29
> **cliffordmt said:**
> Just want to add to this thread about my experience...

I recently upgraded to 9.04 and, as soon as I did, Firefox became almost unusable.  The root of the problem was the ati driver settings, just as described in this thread.  I'm using a Dell Latitude D600 laptop with the ATI Mobility Radeon 9000 graphics card.

It turns out that as of version 9.04, the ati driver now has a different default for the acceleration setting.  Reverting to the old default setting solved the problem for me.  Here are my steps if interested:

Opened the X Window system's configuration file:
```
sudo gedit /etc/X11/xorg.conf
```Added the following in the [FONT=Courier New]Section "Device"[/FONT]:
```
Option        "AccelMethod" "XAA"
```Saved the file are restarted the system.  Firefox performs beautifully now!

This solution also worked for me.

Also using a Dell Latitude D600 with 9.04.

---

### Post by kford on 2010-02-02
```
Option        "AccelMethod" "XAA"
```
Despite this thread's age, I had this problem, today, on a fresh install of 9.10.  This worked wonderfully, thanks.  (I'm running an Intel with an ATI card.)

---

### Post by jolig on 2010-06-24
"XAA" option worked for me as well :)

---

### Post by graytron on 2010-11-07
I'm running Ubuntu 10.04 server edition on an Intel Xeon quad core + ATI Radeon HD 4670 system with Compiz 3D composition and EXA 2D acceleration  enabled.

Firefox scrolling is noticeably sluggish if there are _any_ other fullscreen windows besides the firefox window. If I unmaximize all other windows, firefox scrolls like a charm.

Anyone have similar experiences?

---

