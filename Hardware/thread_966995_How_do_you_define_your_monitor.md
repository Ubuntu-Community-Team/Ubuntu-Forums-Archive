---
title: "How do you define your monitor"
date: 2008-11-01
forum: Hardware
---

### Post by PendragonUK on 2008-11-01
How do you define your monitor, or how to live with the Black Screen of death and not run screaming for the hills. Or at least not reaching for you Windows install disk...

I have run in to an old problem, My LCD monitor is unhappy with modern Linux. 

In the bad old days of installing Linux it was often criticized for forcing users to spec their monitor. I would love to be asked right now. Yesterday I installed 8.10, the first time installing on this PC for a year or two.

8.10 installs just fine but when I install the nVidia driver, after re-boot I faced by a black screen at login. Now I'm sure that the driver is installing properly, I have tried so many different ways. So this isn't a driver problem, this is a monitor detection problem. 

A few years ago when faced by this problem it was simple enough to edit the xorg.conf file. There I could specify the horizontal and vertical, resolution and rez. From there I would have a working system. Thing is now ubuntu doesn't use that file in the same way now. What you edit there may not be used by the OS.

I know the detection is wrong because it says I have an 18" 1280x1024 60MHz. in reality it's 17" LCD 1280x1024 75HMz

So what I need to know is how do I force ubuntu to use the information about my monitor and stop trying to detect then damn thing wrong...

---

### Post by PendragonUK on 2008-11-03
is there no answer to this?

---

### Post by mcclown on 2008-11-03
> **PendragonUK said:**
> is there no answer to this?

I don't really have an answer for you just a suggestion of where to go look. 8.10 has moved to a newer version Xorg known as bulletproofX.....obviously you're not finding it so bulletproof. I'm not sure what has changed confiuration wise because of this but if you do some googling with regard to configuring bulletproofX you might have some joy

---

### Post by PendragonUK on 2008-11-04
Thanks for your reply, I'm off googleing... I'll report back anything I find... :KS

---

### Post by PendragonUK on 2008-11-04
What I have found so far...

bulletproofX is a sort of fall back configuration that should jump in if there are any problems.

Also something is missing from from 8.10 that was in 8.04. That is displyconfig-gtk the one tool that might have helped. 

As I have said I don't think it's a driver issue. I'm using the vesa driver and the monitor is working more by luck than judgment. Ubuntu simply has not detected the monitor correctly. The "Screen Resolution" thinks I have an 18" monitor. Who has an 18" monitor??? 

If only I could specify the horizontal and Vertical, size and refresh rate...

---

### Post by PendragonUK on 2008-11-05
I hate doing this but... bump!

---

### Post by Impact4ever on 2008-11-05
The same problem here!

---

### Post by kamillozo on 2008-11-05
I've got same problem with correct detection of my display.

I want old editable xorg.conf and old dpkg-reconfigure -phigh xserver-xorg working.

This new bulletproofX is a crap! Why to change good things for worse?

---

### Post by PendragonUK on 2008-11-06
I'm slowly coming to the conclusion, I must downgrade.

---

### Post by wgrant on 2008-11-06
Have you tried [the resolution fixing documentation](https://wiki.ubuntu.com/X/Config/Resolution)?

---

### Post by PendragonUK on 2008-11-06
Thank you for your time, I'll investigate and report back.

---

### Post by PendragonUK on 2008-11-06
From what I can see this allows you to to set the resolution and refresh rate of the output to the monitor. I think what I need to be able to do is to define the frequency for the (horizontal and Vertical) for my monitor. Monitor detection has messed up some as it has my monitor size wrong.

Monitor spec:

Active Matrix colour TET LCD
Screen Size 337.9 x 270.3 (17.0")
Pixel Pitch 0.264 (H) x 0.264 (W)mm
Frequency H 31~81KHz V 56~75Hz
Max Pixel Rate 100MHz
Resolution 1280 x 1024 @ 75Hz
15 pin D-Sub

xrandr output

```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1600 x 1600
VGA1 disconnected
DVI1 disconnected
VGA2 connected 1280x1024+0+0 360mm x 270mm
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      75.0*    60.0  
   1440x900       59.9  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1152x864       85.1     85.0     75.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     85.0     75.0     75.1     75.0     70.1     60.0     60.0     43.5  
   960x720       120.0  
   928x696       120.1  
   896x672       120.0  
   960x600       120.0  
   832x624        74.6  
   960x540       120.0  
   800x600       140.0    130.0    120.0     85.1     72.2     75.0     60.3     56.2  
   840x525       149.9    139.8    120.0    119.8  
   800x512       120.3  
   700x525       149.5    140.1    120.0  
   640x512       170.0    150.0    120.0  
   720x450       119.8  
   640x480       170.2    120.0     85.0     75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        87.8     85.0     70.1  
   680x384       119.6    119.9  
   640x400        85.1  
   576x432       170.3    170.2    150.0    150.0    140.0    120.1  
   640x350        85.1  
   512x384       170.0    150.1    140.1    120.0  
   416x312       149.3  
   400x300       170.5    144.4  
DVI0 disconnected

```

Back in the day I would have put in the Frequency during install and all would be well, but times have changed...

One point that might be worth investigating with all of these people reporting issues like this is, how many are using DVI to D-Sub converters. People with up-market Video cards with DVI only output but running non-DVI monitors and using the adapter plugs supplied with their cards. Would not the card say it had a DVI output but the monitor not respond in the correct way therefore messing up the monitor detection?

---

### Post by zaine_ridling on 2008-11-06
Well, I've got a black screen upon (8.10) login, too, and despite trying everything among several threads on the forum, I'm stuck using an old crappy Vista computer rather than my hot shiny fast Linux one. (And I ain't switching to another distro.)

A real bummer.

---

### Post by PendragonUK on 2008-11-07
I'll stick with it, there must be a solution. Something buried in the gtf or cvt that can allow me to tell ubuntu what size monitor I'm running. Then getting the resolution and refresh rate should be easer to define.

---

### Post by PendragonUK on 2008-11-07
I have read through the "man's" for gtf and cvt. they are both about resolution not screen size.

I'm sure that once it knows the screen size I will be able to do the rest.

---

### Post by PendragonUK on 2008-11-13
I have given up! the partitions have been deleted and XP Pro x64 installed.

I'm still running ubuntu on my laptop, but I'll have another look if and when I get a different monitor for my desktop PC. I put 20 to 30 hours in to trying to solve this problem with no luck.

There is something strange about my monitor that ubuntu just dosn't like. It's not just limited to ubuntu, in the past week or so I have tryed Fedora 9 and OpenSuse, they also had the same problem with my monitor. Strange how Microsoft dosn't have a problem. In the last few weeks I have installed more times than I care to mention. Both Vista 64bit and what I'm running now XP x64 have had no issues with it. 

In the past Linux was heavly critsied for having overly complicated instal. It's almost as if the community has over compensated and made it too easy. Removed all and any referance to hardware specifcation to the point that if you do know that you have something unsual in your box you don't get a chance to set it up correctly.

---

