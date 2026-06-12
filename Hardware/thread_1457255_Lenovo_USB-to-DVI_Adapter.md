---
title: "Lenovo USB-to-DVI Adapter"
date: 2010-04-18
forum: Hardware
---

### Post by voz on 2010-04-18
I am trying to install a Lenovo USB-To-DVI Adpater using a Thinpad X61 and Ubuntu 64bit 9.10(karmic). So far I only found this:
[http://lists.freedesktop.org/archives/libdlo/2009-August/000305.html](http://lists.freedesktop.org/archives/libdlo/2009-August/000305.html)

It is supposed to be a manual how to get it running by using a displaylink driver, but as I am new to Linux I just don't how to do it.

---

### Post by mac2linux on 2011-03-24
I just followed the instructions here:

[http://libdlo.freedesktop.org/wiki/](http://libdlo.freedesktop.org/wiki/)

and my DisplayLink USB to DVI is now working.

---

### Post by fraktalek on 2011-07-30
@mac2linux how did you do that? Does it work without cloning? Xinerama or RandR? On Ubuntu 11.04? What card is your main graphical card?

I'm trying to get it to work on Ubuntu 11.04, on the Intel SandyBridge graphics and the Lenovo (DisplayLink) USB-to-DVI adapter with no luck at all. 

I managed to get at least two monitors with one of them cloned on the notebook's LCD with a setup similar to Steve Hanov's: [http://askubuntu.com/questions/40031/how-do-i-use-a-displaylink-monitor/40665](http://askubuntu.com/questions/40031/how-do-i-use-a-displaylink-monitor/40665) but I can't get the ZaphodHeads option to work with the intel driver. 

Anyway, the best one can hope for now is probably just a 16 bit configuration on all displays without any 3D (i.e. with Unity 2D), with Xinerama (moving windows between monitors) working, right?

---

### Post by fraktalek on 2011-07-31
I have now spent two and a half days trying to setup my ThinkPad T420 and two Samsung LCDs in a triplehead (multihead) configuration. I have the T420 without Optimus, so I have only the Intel SandyBridge graphics plus the Lenovo USB-to-DVI adapter.

My experience is that it is not possible to configure all three displays using one X server (i.e. multihead) because of various problems: the intel driver probably does not recognize ZaphodHeads so it is not possible to get rid of cloning...even with Xinerama disabled I could not get it to work, xRandR support in the intel driver is probably not full. It didn't work even if I compiled the latest udlfb kernel driver and the displaylink X driver (and I tried it all: display link as the primary screen, different order of the device declarations in the xorg.conf, with zaphodheads, without zaphodheads, with Virtual, without Virtual in the Display subsection, fbdev driver, displaylink driver, different depths, ...). The biggest achievement was having the two Samsung displays running Unity 2D in 16 bit with one of them cloned on the laptop's LCD.

The only way I managed to have three independent displays was using a *multiseat* configuration (i.e. two or more X servers in my case), similarly to the following thread: [http://ubuntuforums.org/showthread.php?t=1313190](http://ubuntuforums.org/showthread.php?t=1313190)

Note that the ServerFlags and keyboard and mouse options in the xorg config are necessary, otherwise x2x behaves strangely.

Unfortunately, I did not succeed in achieving the "official" recommended multiseat configuration: [https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX) 

Anyway, the advantage of the configuration I now have is that I can run the normal dualhead (laptop+1 LCD) in full 24bit (the intel driver apparently doesn't support 32bit) and with Unity 3D (compiz). The second Samsung LCD is then managed by a second X server running on display :1 in 16bit and no 3D.

---

