---
title: "What's the best machine to run Ubuntu."
date: 2008-08-29
forum: Hardware
---

### Post by maxmanapple on 2008-08-29
Hi there!
Here are my questions.

1. My computer has two GPU's: an ATI Radeon 9200 (128 MB) and a "some-brand" 32 MB on-board. Despite the GRAM amount, which of those would perform better with Ubuntu?

2. I've heard that P4 processors create a lot of heat which degrades the machine's performance, and I recently found an old and still working Pentium III (700 MHz) chipset. So my question is: Is Ubuntu going to work on PIII? And what are the differences between P4 2,5 Ghz and PIII 700 Mhz (beyond the obvious)?

---

### Post by LaRoza on 2008-08-29
> **maxmanapple said:**
> 
1. My computer has two GPU's: an ATI Radeon 9200 (128 MB) and a "some-brand" 32 MB on-board. Despite the GRAM amount, which of those would perform better with Ubuntu?

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

I see the ATI driver listed, so it should work better than the integrated.

> 
2. I've heard that P4 processors create a lot of heat which degrades the machine's performance, and I recently found an old and still working Pentium III (700 MHz) chipset. So my question is: Is Ubuntu going to work on PIII? And what are the differences between P4 2,5 Ghz and PIII 700 Mhz (beyond the obvious)?
The P4 will work better than the P3. The P4 is a hotter and more power hungry processor, but it is way better than the P3, although Ubuntu would work on it, I don't see the point. The P3 is also a hot processor as well.

Have a good heatsink and fan, and you shouldn't have to worry about it. (The P3 requires a heatsink and fan also)

---

### Post by nicedude on 2008-08-29
Umm I don't know does anyone know if there is a version for a cray :-)

---

### Post by maxmanapple on 2008-08-29
> **LaRoza said:**
> 
I don't see the point. The P3 is also a hot processor as well.

Have a good heatsink and fan, and you shouldn't have to worry about it. (The P3 requires a heatsink and fan also)

I'm a little in doubt because of a documentation

[QUOTE=Wikipedia]
Pentium 4-C - 2.4 GHz - 67.6 W - 35.5
Pentium III - 700 MHz - 18.3 W - 38.3[/QUOTE]

The final number stands for Speed:Power ratio in Mhz/W. The numbers in the PIII seem more efficient than P4.

While my PIII case remained cold (when I used him back in 01), I can fry eggs on my P4. Also, my PIII case is more spacious and air-fluent than P4 case, and the PIII case and has a front fan (helps delivering the cool air) So, my question remains.

---

### Post by estyles on 2008-08-29
You could probably run Ubuntu on a P3, minus the eyecandy.  But only if you're planning on doing something else with the P4.  It would be silly to opt for the less powerful (by far) machine just because of power concerns.  Get a better heatsink, or some case fans.

---

### Post by maxmanapple on 2008-08-29
> **estyles said:**
> You could probably run Ubuntu on a P3, minus the eyecandy.  But only if you're planning on doing something else with the P4.  It would be silly to opt for the less powerful (by far) machine just because of power concerns.  Get a better heatsink, or some case fans.

There's the problem. All of my cooler fans are in the P III box and neither the chipset nor the fans are interchangeable. So my P4 has two fans (heatsink and power source) and my PIII has 4 (heatsink, power source, front and rear case). Is it still worthy?

---

### Post by mike1234 on 2008-08-29
> **nicedude said:**
> Umm I don't know does anyone know if there is a version for a cray :-)

 This one should be okay.

M.

[http://static.cray-cyber.org/General/LARGE/Cray_YMPEL_Portrait.JPG](http://static.cray-cyber.org/General/LARGE/Cray_YMPEL_Portrait.JPG)
[http://www.cray-cyber.org/general/start.php](http://www.cray-cyber.org/general/start.php)

Free software installed (/usr/local): 	Bash, GNU Make, Readline, GZip, less, vim, unzip, GNU tar, xaos, perl (in /opt)

---

### Post by SunnyRabbiera on 2008-08-29
> **LaRoza said:**
> 
The P4 will work better than the P3. The P4 is a hotter and more power hungry processor, but it is way better than the P3, although Ubuntu would work on it, I don't see the point. The P3 is also a hot processor as well.

Actually my P4 is very efficient but I think its because its a later model.

---

### Post by maxmanapple on 2008-08-29
> **SunnyRabbiera said:**
> Actually my P4 is very efficient but I think its because its a later model.

Mines are 1999 (P III) and 2003 (P4). The PIII was relatively fast with Win98 while XP on P4 was always slow as hell. Now I have Ubuntu and it remains somewhat slow.

---

### Post by SunnyRabbiera on 2008-08-29
> **maxmanapple said:**
> Mines are 1999 (P III) and 2003 (P4). The PIII was relatively fast with Win98 while XP on P4 was always slow as hell. Now I have Ubuntu and it remains somewhat slow.

Well my processor was probably made in the same year as my PC (in 2006), I suspect its a cedar mill.

---

### Post by Canis familiaris on 2008-08-30
Well if you need a minimal system say a command line only or system with IceWM which you wish to use as a router, file server, etc., and maybe some internet surfing, I think Pentium III would be better because it would save power. However it will be slow.
Pentium IV would be a better bet if you plan to use it daily. However it gets pretty hot particularly those Prescotts.
As for those stats, those are stats for perofrmance per watts. Yes Pentium III is indeed better in that regard but in terms of pure speed Pentium IV is better.

If you are purchasing a new system I would suggest to steer clear of the second Hand Pentium IIIs and IVs and go with Semprons (assuming minimal budget) since they are cheap and perform well.

---

### Post by blucht on 2008-09-11
> **maxmanapple said:**
> 
2. So my question is: Is Ubuntu going to work on PIII? And what are the differences between P4 2,5 Ghz and PIII 700 Mhz (beyond the obvious)?

As has been hinted at, the short answer to your question is yes, Ubuntu will work on your PIII. Your best bet to get any kind of reasonable performance is to use a lightweight desktop environment or window manager (Xfce, Fluxbox, etc) instead of the resource-heavy Gnome/KDE. As a point of comparison, I was running Ubuntu as a media centre on a 800 MHz Celeron for a while and it had no problem with basic web browsing and audio/video playback in Xfce. Gnome worked, but s...l...o...w...l...y; using it was an exercise in patience. That's if you need a GUI at all. The same machine is currently headless and running as a web, email, file server, and torrent machine and is very happy.

I should note, though, that the processor is not the end of the story. You also need enough RAM. My machine had 256 MB and I wouldn't want to run Ubuntu on anything less. That necessitated the use of the alternate install CD, too. To use the Live CD installer, I think the minimum is ~380 MB.

---

### Post by prsinghdua on 2009-09-28
I have a P3 through which I am typing right now and it runs a lighter edition of ubuntu called xubuntu. It had Windows 2000 before but it was slow as hell. So I switched and found it to be amazingly fast! :)

---

### Post by quazisayeed on 2010-07-01
is my machine 

Acer Aspire 3640
Processor Intel Celeron M 410 1.46GHZ
Motherboard Phonix 
AGP: ATi Raedon X200M
RAM: 1GB
HDD:60GB
OS: willing to use Ubuntu 10.04

need suggestion....Ubuntu is supported for this spec.

---

### Post by estyles on 2010-07-01
Why dredge up a 2-year-old thread (which someone inexplicably dredged up a year ago for no reason) instead of posting a new thread with your question?

---

