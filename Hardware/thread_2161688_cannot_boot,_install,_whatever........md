---
title: "cannot boot, install, whatever......."
date: 2013-07-11
forum: Hardware
---

### Post by jgw on 2013-07-11
I think this is a hardware problem.  I recently installed 12.04.2 and was messing around.  I re-booted and it said that the cpu had stopped for 20 seconds and proceeded to examine memory.  I let that run all night and it just kept on.  then I turned it off and back on and, this time, I have a box on the screen with two vertical boxes plus one horizontal one at the bottom.  The two vertical boxes are for data and prog and there is no label on the bottom one.  the data box has (lines 0, 1, 2) 0:2d5.9  1:5b05.5 2:4625.a   The vertical box has Err 2 then IP 2b43:    3128.d

I tried to boot from the dvd and it tries but then the above comes back.  

I have no clue (surprise!!)

Thoughts?

Thank you...............

---

### Post by oldfred on 2013-07-12
If you right click does anything happen?

What video card/chip do you have?

Have you tried nomodeset from grub menu?
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by jgw on 2013-07-12
Thank you for the reply.
The current display card is, basically, a radeon 9200se

The first notification I got was; 
graphics initialization failed
error setting up gfxboot
Boot:

Its obviously waiting for input but everything I can think of to enter there results in the strange box thing or nothing.

The strange thing is that it was working just fine.  I was testing the video with xbmc (if it works there ..........) I was in the throes of bringing up xbmchub stuff in xbmc when this occurred.  I can only assume I screwed something up bigtime.  I then decided to simply re-install and make another run at it and that is when all this stuff began.  Now I can't even get to the dvd.  I thought I might have been the dvd so I burned myself another one - didn't help.

I also tried the following.  Switched video from the radeon 9200 to the built in video (VIA S3 UniChrome).  Same problems.  Then I put in another board (msi - radeon 9700) Same problem yet again.

---

### Post by BreezyBrooke on 2013-07-12
What are your full pc specs? It sounds like the computer is instantly booting to a Bios-like screen. Hence why no matter what you put in, it boots to that screen.

---

### Post by oldfred on 2013-07-12
How old is video? I am not familiar with ATI/AMD but that model is not on list of old models they have discontinued support for.
And if system it that old how much RAM. Full Ubuntu needs more RAM than minimum specs. Then Xubuntu or Lubuntu would work better?

       [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)


 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)
On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

---

### Post by maglax on 2013-07-12
I was never able to boot of the regular install because of a ubi-partman error. How I got around it was using the alternate installer.  So try that.

---

### Post by Yellow Pasque on 2013-07-12
If your BIOS has memtest built into it, run that. You can also burn memtest to a CD and run it that way (parted magic is a  good ISO for that)

---

### Post by jgw on 2013-07-13
The motherboard is a via p4m800 running, if I remember correctly, at 2.8mzh. The machine has 1.5gb of memory.  Switched video from the radeon 9200 to the built in video (VIA S3 UniChrome). Same problems. Then I put in another board (msi/amd - radeon 9700) Same problem yet again. 

Let me also repeat.  This thing was working just fine until I put xbmc onto it and then tried to install xbmc hub    After that it was all downhill.  I suspect that its a hardware problem because it said, at the very beginning, that the cpu had stopped for 22 seconds and then went into examining every byte of memory (with no apparent resulting errors).  After that I rebooted and it came up with a boot menu that had some options.  I choose the one to fix (forget what it wanted to fix but it seemed reasonable at the time <g>)  After that it was all downhill.  

I really appreciate all the responses.  I also appreciate the suggestions although many cannot be used simply because I cannot get to the system to do that.  The same with the cd/dvd as it will not even boot from there (dvd).

The problem with using the alternate install is that I do not seem to be able to boot off the cd/dvd anymore.  (irregardless of bios setting - this whle thing is REALLY dicked!!)

I have to go away for a couple of weeks.  When I return I think I will swap out this motherboard for another and, this time, use a better video card (more recent).  I think I will also replace the drive with one that has been freshly formatted before anything else just to see if I continue to get all these errors.  If that happens then I think its safe to say that this is a hardware error as I don't think that ubuntu/linux is going to somehow automatically start messing with the bios.

Anyway, thanks, again, for all the responses!

---

