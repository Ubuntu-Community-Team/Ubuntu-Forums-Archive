---
title: "Likely issues with a Lenovo Thinkpad T410?"
date: 2011-02-23
forum: Hardware
---

### Post by grey.skylark on 2011-02-23
I'm considering buying a Thinkpad T410i or T410 to run the most current version of Ubuntu.  I've been reading through the forums about possible issues, particularly re: switchable graphics and the Realtek wireless card.  I'm a bit overwhelmed by the potential problems.  

What options would you recommend to minimize graphics, wireless, and other issues?  Thank you!

**Processor**
Intel Core i3-370M Processor (2.40GHz, 3MB L3, 1066MHz FSB) 
[add $30.00] Intel Core i3-390M Processor (2.66GHz, 3MB L3, 1066MHz FSB) 
[add $45.00]Intel Core i5-480M Processor (2.66GHz, 3MB L3, 1066MHz FSB) 


**Graphics**
*T410i*: Intel Graphics Media Accelerator 5700MHD - AMT

*T410*:#
Intel Graphics Media Accelerator 5700MHD - AMT
OR

NVIDIA NVS 3100m Optimus Graphics 512MB DDR3 with AMT
NVIDIA discrete (dedicated) graphics feature a dedicated graphics processor and memory for superior performance.
[add $100.00]


**Memory**
2, 3, or 4 GB of ram - Definitely leaning towards 4.


**Wireless**
ThinkPad bgn Wireless [$0.00]
Intel Centrino Wireless-N 1000  [add $20.00]
Intel Centrino Advanced-N 6200 (2x2 AGN) [add $40.00]
Intel Centrino Ultimate-N 6300 (3x3 AGN) [add $55.00]
Intel Centrino Advanced-N + WiMAX 6250 





More info:
Mostly I will use it for web browsing, listening to music (streaming & downloaded), word processing, and watching video (streaming, downloaded, & on DVD).

I'm still an Ubuntu beginner and I really would like a solid computer that runs Ubuntu without frequent major issues.  Some troubleshooting is fine and to be expected.  I'm currently running 10.10 on an old Powerbook, so have gotten used to researching, troubleshooting, and using the command line. 

Why a Thinkpad?  I like the reliability, tough case, matte screen, and the simple design of the Thinkpads.  Some of my friends have been running Thinkpads for 5+ years without much effort beyond basic upgrades.  


Thanks again!

---

### Post by cyberey66 on 2011-02-24
For ram, Newegg has some pretty good sales on DDR3 now.  You can get a 4GB stick for $27.  An option if you want to upgrade it yourself.

For more info on specifics, I would checkout the thinkwiki site, [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

For graphics,  I have a W500 with switchable graphics, and when I use the discrete option, I consume about 50% more power (~30W vs ~15-20W) so you lose some battery life.  That is something to consider.    If you do go for switchable graphics, I wrote a script that detects what card I am using at boot and selects the appropriate graphics driver so I can switch between the two.  The script is for ATI drivers, but can be easily adapted for nVidia if you are inclined to do so.   Intel integrated graphics seem to work well out of the box and from my personal experience over the years, the support for nVidia chipsets is superb.  I always pick nVidia if I have the option.

And I agree, Thinkpads are great.  I purchased mine solely for the build quality and screen.  I was debating between a Macbook Pro and a ThinkPad.  The ThinkPad was cheaper for similar specs and offered a matte WUXGA screen in a 15.4" laptop!  Screen quality has sadly become regressive.  I don't understand how my 5 year old Dell has a much higher quality screen than anything offered by them now, but that's another story.  Good luck!

***EDIT  I stand corrected! Regarding the optimus card, read this, [http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660) .  I guess my personal experience is becoming a bit dated.

---

### Post by KnightZero77 on 2011-02-24
The Intel HD graphics are more than decent if you aren't planning on doing any heavy 3d.  Compiz runs smooth as silk on my X201.

I heard bad things about the Thinkpad B/G/N adaptor and compatibility with Linux, so I went for the Intel Wireless-N 1000 to try to avoid it.  A word of warning, if you do intend to use the OEM supplied Redmond born operating system, the Intel card is an absolute pain (not working after suspend/resumes without a reboot, randomly disabling itself when changing wireless networks, etc).  However, I've seen no problems in 10.04 or 10.10.  If you must dual boot, make the jump to the 6200 or 6300 card for WAN.

Also, these days, 4 gb of memory is a bare minimum, not to mention quite cost effective.  I wouldn't install any less, and I'd swing for the single chip so that you can double it in the future, if your needs expand.

Lastly, depending on your budget and your need, waiting for the new Sandy Bridge refresh (T420) might be a worthwhile option.  I've been hearing battery life numbers that put my X201's 9 cell life of 8-12 hours to shame.  I think the T420 is quoting 15 hours on a single charge, up to 30 with the full battery expansion (Sacrificing the DVD-ROM for a bay battery, IIRC).

---

