---
title: "Foxconn barebones issue"
date: 2009-10-15
forum: Hardware
---

### Post by wilkinsonrb on 2009-10-15
I recently purchased a Foxconn SFF R10-S2 barebones system to build a HTPC. I have installed 2Gb of RAM and a 250Gb sata Hard drive. It is connected to a 46 inch Samsung tv/monitor. 
I have tried both ubuntu 9.04 and crunchbang linux, and encountered the same issue. The CPU typically runs at 100% usage and after a few minutes it just shutdowns. No warnings or otherwise. There is little information concerning this boards performance with Linux. Is there anyone else having issues or been successful using this hardware?
Does the size of a monitor affect the performance of X?
Do I need to flash the BIOS or try another OS. I will attach the unit to a 20 inch lcd to see if there is a difference.

---

### Post by kerry_s on 2009-10-15
i had the r10-s4 dual-core, it ran perfectly.

i don't think its meant to run screens that big, but you can try setting the shared memory to a fixed size in the bios, if i remember right the normal is set to auto, meaning it grows a shrinks. i had mine set to the max size.

---

### Post by wilkinsonrb on 2009-10-25
Thanks for your help kerry_s. It seems that the unit is underpowered. I have installed a semi-decent video card. Same issues. I have the settled on the box as a simple server. 
Thanks for your help.

Robert

---

### Post by kerry_s on 2009-10-25
> **wilkinsonrb said:**
> Thanks for your help kerry_s. It seems that the unit is underpowered. I have installed a semi-decent video card. Same issues. I have the settled on the box as a simple server. 
Thanks for your help.

Robert

even with the 20" screen? i just got my foxconn rs233 last week, same as yours just difference in case & it was on sale $86.99, i'm running it on a 19" screen 1280x1024, runs fine here. in the bios i set video to fixed & 128mb max.

---

### Post by gordboy on 2009-10-26
I just got an R10-S4 and am returning it as defective. we'll see if the replacement newegg is sending will be any better. my issue is the system would freeze as soon as i tried to do anything.

i could install ubuntu with no problem, also can boot from a live memory stick with the HDD disabled, but as soon as i try to open firefox (or anything else) it completely freezes, no keyboard response (eg ctrl-alt-del, -bksp, -F6). 

I was hoping it was bad RAM, but trying known good modules didn't help.

interesting, though, memtest86+ for both my memory sticks registered as DDR 354 (177Mhz), definitely not what i expected. @kerry_s, have you run memtest and do you recall what speed it told you?

---

### Post by kerry_s on 2009-10-26
> interesting, though, memtest86+ for both my memory sticks registered as DDR 354 (177Mhz), definitely not what i expected. @kerry_s, have you run memtest and do you recall what speed it told you?

nope, had no need to.

in my r10-s4, that dad took, i'm running 2gb pc2-6400, it's backward compatible.

in this new rs233, i just have 512 pc2-5300, cause its all i had. i'll upgrade it later, if i find the ram on sale.

---

### Post by gordboy on 2009-11-06
> **gordboy said:**
> I just got an R10-S4 and am returning it as defective. we'll see if the replacement newegg is sending will be any better. my issue is the system would freeze as soon as i tried to do anything.

i could install ubuntu with no problem, also can boot from a live memory stick with the HDD disabled, but as soon as i try to open firefox (or anything else) it completely freezes, no keyboard response (eg ctrl-alt-del, -bksp, -F6). 

I was hoping it was bad RAM, but trying known good modules didn't help.

interesting, though, memtest86+ for both my memory sticks registered as DDR 354 (177Mhz), definitely not what i expected. @kerry_s, have you run memtest and do you recall what speed it told you?

i got the replacement and am having the same issue. not sure what to try now, it's hard to believe that both systems would be defective.

---

### Post by kerry_s on 2009-11-06
> **gordboy said:**
> i got the replacement and am having the same issue. not sure what to try now, it's hard to believe that both systems would be defective.

:lolflag:
are you that unlucky?

are you using ddr2-533 compatible ram?
did you go crazy in the bios?
did you ground yourself before messing with the internals?
have you tried a different distro? from jaunty on the intel drivers screwed on mine, it's an acer lcd problem, i been using debian lenny on mine.

---

### Post by bd92154 on 2009-11-07
> **gordboy said:**
> i got the replacement and am having the same issue. not sure what to try now, it's hard to believe that both systems would be defective.
 Time for me to chime in... I think I have an answer/ non-answer for you:
That is provided you are loading the newest and best 9.10 version of UBUNTU on your system.
 
Short version: My system FOXCONN SFF R10-S4 /Memory 1GB DDR2/Hard Drive 500gb WD
 
All tested SAT/ Reformatted Hard Drive on each load.
 
Loaded 9.10 UBUNTU does everything, but run after you use the mouse for a click or so.  Sometimes you can't even get the mouse to run.
 
Loaded 9.04 UBUNTU... No problems whatsoever with the mouse or running programs.  Well I am having some trouble getting the computer to talk via the installed network card to my dLink 855 router, but I'll work on that.
 
So here is my answer... Load 9.04 and see if that makes your problems go away.

---

### Post by snowpine on 2009-11-07
I've been running 9.04 lpia for a couple of weeks with no problems. 9.10 doesn't work unless you disable compiz effects. (Freezes a few seconds after login if you move the mouse or open any windows.)

---

### Post by imcdona on 2009-11-08
I am running into the same problem. The system freezes after I try clicking something. I am running a Foxconn R20-S2 Intel 945GC. The system ran fine with 9.04.

How does one go about disabled compiz from the command line? I am unable to do it from the GUI without the system freezing.

---

### Post by kerry_s on 2009-11-08
you need to get into the rescue mode & add " "Driver" "vesa" " to the Device section, that will automatically disable effects.

my advice, don't waste your time, the intel drivers are screwed. use a version that worked or a different distro. i'm using debian lenny on my foxconn rs233.

---

### Post by markellse on 2009-12-26
This is a reported bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/456902](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/456902)

It is a problem with the video driver for the Intel chipset that the Foxconn R10 uses. 

Ubuntu 9.04 works fine. There are problems with both 9.10 and 10.04 alpha.

It's a great pity because the Foxconn boards are beautiful and work perfectly with 9.04. I have loads of them deployed where I work.

---

### Post by kerry_s on 2009-12-26
> I have loads of them deployed where I work.

are they running windows 7 ?
it works like a champ, everything is supported out of the box, no drives needed.

---

