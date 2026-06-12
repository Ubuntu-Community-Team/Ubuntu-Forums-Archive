---
title: "ATI graphics tearing"
date: 2010-02-20
forum: Hardware
---

### Post by tntc on 2010-02-20
I have a 512MB ATI Mobility Radeon HD 4570, and had the same problem with my other laptop with an X1400.  No matter what settings I use, I get minor tearing that rolls down my screen.  This includes moving Compiz windows, watching video in any player, running glxgears, watching flash, and anything else that causes motion on the screen.

Basically, if something is moving on the screen, there is a line of tearing that will eventually run through it.  This tearing runs gradually down the screen.  When it reaches the bottom, it starts back at the top again.  It's somewhat like what happens if you turn off Sync to vblank in compiz and move a window around, or set up compiz with the wrong refresh rate.

I've tried the following:
-Sync to vblank on AND off in compiz using fglrx AND radeon (with upgraded 2.6.32 kernel and graphics drivers)

-Sync to vblank on AND off in the fglrx driver

-Changing monitor refresh rate via compizconfig-settings-manager to 60hz (reported refresh), 120hz (double refresh), and 180hz (triple refresh).  180hz showed some improvement, but the tearing was still present.

-disabling Desktop Effects/compiz

None of these have gotten rid of the tearing enough that I don't notice it.  Most of my google-fu has turned up stuff about tearing JUST in video playback with the Xv extension, but this tearing seems unrelated.  The tearing does not occur in Windows 7.  In order to get the open-source ati/radeon/radeon HD driver installed, I followed the directions for Group Two cards in the [Community Documentation]("https://help.ubuntu.com/community/RadeonHD").  I have since re-installed from scratch (and the problem remains)

System Specs:
Ubuntu 9.10 x64
Dell Studio 1555
512MB ATI Mobility Radeon HD 4570
Intel Core 2 Duo T9550 2.66GHz, 1066Mhz, 6M L2 Cache
3GB, DDR2, 800MHz 2 Dimm
15.6 Inch Full HD(1080p) High Brightness LED with TrueLife (1920x1080 max resolution, 60hz)

---

### Post by andrewbrown22 on 2010-02-20
Sorry to be of no help, but I'm having what seems to be similar issues with my newly purchased Radeon HD 4550 by MSI.  (Not to mention that my full HD TV won't project the full 1080p image correctly--TV issue however, not the cards fault)

Is there any solution to this?  I picked ATI over an Nvidia card because of the support for HDMI audio out without any hardware configuration, but I'm now wondering if my decision was a good one..

---

### Post by tntc on 2010-02-20
Well, simply by stating "Me Too!" you're being a help.  I'm tempted to try Lucid on that guy just to see if the newest of the new fixes the graphics issues.  I will update further if I do and it does.

---

### Post by Bastien BB on 2010-03-20
Hi

I am having screen tearing issues while playing video in VLC. I am using ubuntu karmic on a dell studio 1558 with a ATI radeon mobility 4570. I use windows 7 on the same computer and everything works fine there. 
I tried all the solutions I could find on various forums until now bit nothing worked that far...

Thanks for any help! :)

---

### Post by mellowtothemax on 2010-05-14
I can also confirm this problem.  I have tried every possible suggestion and still no luck.  Using the radeon driver fixes the problem but the proprietary driver from ati always has this issue.

Dell Studio XPS 1640 ATI 4670 Ubuntu 10.04

---

### Post by Alpha_Cluster on 2010-05-14
I also having these issues I am using a 5770. The only good new I have to shed on this right now is that it has been happening for a long time with ATI's driver but I did notice in the April release notes there was finally a "Known Bug" that showed up that sounds to be covering this issue so maybe we ATI users might finally get some tear free love in the next version of the driver. Of course supposedly we are already using it if we have 10.04 but hey I can wish still right? I can say that at least we can now be happy that the X server doesn't seem to hang anymore with ATI drivers when switching to the F1-F6 consoles now. :) Being optimistic here.

---

### Post by shebaw on 2010-05-29
The proprietary driver for ATi Radeon hd 4570 is trash, PERIOD! The only thing that fixed the tearing was updating to Lucid, the open source driver is way better than the proprietary driver on Lucid.

---

### Post by emergence on 2010-05-30
I have 10.04 and have attempted the same steps the OP did. I am still suffering from this issue. Tearing when windows are moved, video is played etc... I have an ATI HD5850 and have just did a fresh install of 10.04.

My google fu revealed that this is a bug with fglrx (don't have the ubuntu bug link on hand).

---

### Post by SeePU on 2010-05-31
What settings are you using?   What do you have turned on/off?

I read if you use for output:
xv - will get tearing
GL - won't get tearing

enable vsync but turn off Compositing/Compiz (turn off desktop effects if you still have issues)

Try those and see if it helps...

If you want a certain setting but still have problems, pls post whta it is.  I'm curious why you would want that particular setting and pls post what happens...

Experiment with different settings and see what works/doesn't work... Do these suggestions help????:(

---

### Post by theblackbird on 2010-06-01
ATI Radeon 4870 here, same problem. I've tried everything, nothing solves it. 

Setting video output to OpenGL in VLC or any other video players helps, but does not get rid of it entirely. Also, this sometimes results in strange video garbling in full screen mode.

FSAA and Anisotropic Filtering doesn't seem to work either (no matter what I set in the ATI ccc).

It's sad to see that after all these years of AMD's 'dedicated' linux driver support, so little has been accomplished.

---

### Post by bossdak on 2010-06-06
i have a 5770 and it has tearing problem, slow window resize/maximize. i will now go and get me a g210 or 8400 nvidia and see how it goes. there is always something broken in ati drivers.

---

### Post by SeePU on 2010-06-08
> **theblackbird said:**
> ATI Radeon 4870 here, same problem. I've tried everything, nothing solves it. 

Setting video output to OpenGL in VLC or any other video players helps, but does not get rid of it entirely. Also, this sometimes results in strange video garbling in full screen mode.

FSAA and Anisotropic Filtering doesn't seem to work either (no matter what I set in the ATI ccc).

It's sad to see that after all these years of AMD's 'dedicated' linux driver support, so little has been accomplished.Have you tried both fglrx AND the open source radeon/ati driver?

---

