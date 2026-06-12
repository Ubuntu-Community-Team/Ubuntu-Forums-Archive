---
title: "Hardware conflict - GeForce FX 5200 INcompatible?"
date: 2009-04-30
forum: Hardware
---

### Post by JBetts on 2009-04-30
Hello awesome people of the forums.

Interesting problem to those that find this sort of thing interesting:

Was running an Ubuntu 8.10 system perfectly on a very lightweight system; wanted to upgrade the video from onboard to a PCI card (only slot on mobo) in order to stream web video. 

Added a new video card, and whole system borks - 8.10, 9.04, even running both as a live CD in order to recompile all drivers. (Yes, the PCI card is BIOS selected). Taking video card out makes the system live again, but the video card is [definitively listed as compatible]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia").

System:

Mobo:      Intel D945GCLF
Case/PSU:  Apex MI-100 (250W)
Mem:       2 G Kingston DDR2 SDRAM
HDD:       Western Digital IDE 80 G (old but crazy stable)

Tried to add - 

Video:     GeForce FX 5200 ([Chaintech OEM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814145136"))


After the card was added, the system wouldn't load, pausing about a third of the way through the ubuntu loading screen, then would give a huge number of "tty1 respawning too fast" errors. These errors would happen even in recovery mode. This originally occured when I had a DVD player attached as well, so, thinking that voltage might be an issue on the 250W PSU, I unplugged it. That changed the error being received to "Corruption detection in low memory. Low memory corrupted". Can't even get to a command prompt to do an output of error log.

It is similar to the problems experienced by [these]("http://ubuntuforums.org/showthread.php?t=1101673") [people]("http://ubuntuforums.org/showthread.php?t=1039827&highlight=Geforce+FX+5200"). 

Any ideas?

---

### Post by JBetts on 2009-05-03
Looks similar to [this issue]("http://ubuntuforums.org/archive/index.php/t-560695.html"), which is also unresolved as of yet...

---

### Post by bear54 on 2009-05-03
My memory is not what it used to be but I seem to remember a time when I installed a video card in a PCI slot and in the BIOS I had to select the PCI choice for video but I also had to _disable the onboard video_. If this is the case with your motherboard your video would not work until both options are selected. It is worth checking out.
Good Luck
Eric:cool:

---

### Post by JBetts on 2009-05-03
Thanks for the tip Bear, but unfortunately, the D945GCLF only has an option for the DVMT (dynamic memory-stealing off the main board) and an option for which video to use (IGP, PCI or auto). 

Thanks for offering your advice, though!

---

### Post by mojo6911 on 2009-10-16
I have the exact same problem. Same board, only with the PCI 8400GS Sparkle card. Did you ever get it sorted? I have the EXACT same issue.

---

### Post by igknighted on 2009-10-16
Mojo, start a new thread.  The issue the OP had was that the 5xxx series cards were no longer supported by Nvidia, whereas your 8400 is still, so the problems are not likely related.  I think you will get better responses in a new thread.

---

### Post by JBetts on 2009-10-16
No - this issue was never resolved. 

I ended up testing like 3 PCI cards, all of which gave the same kernel panic behavior (though the cards themselves were tested as good). 

I'm thinking it must be a problem specific within the linux kernel to this mobo with PCI video cards...I'm stuck and so basically never got decent video on this box...

Let me know if you have any brainstorms/epiphanies. 

Thanks!

---

### Post by mojo6911 on 2009-10-18
I figured it out. Since you can't disable the onboard video, it conflicts with any PCI video card with linux. This is what I did:

1. Remove PCI card and install Ubuntu using on board video.
2. After it is installed, 

sudo nano /etc/modprobe.d/blacklist 

add:

blacklist intel_agp
blacklist agpgart
3. Shutdown and reinstall the PCI card and boot up and it should work.

---

### Post by JBetts on 2009-10-19
Wow...well that fixed it. Wish I'd known the fix was so simple. Now my scrolling is smooth as can be.


Thanks a bunch mojo6911!!!

---

### Post by Jules Delespy on 2009-12-03
I know this is an aged post, but I found it as I went through much trouble installing on an affected machine, and it is likely others will find their way here in the future.
The issue is installation on machines where 1) graphics processing (Intel) is integrated into the motherboard and 2) a graphics card has been added as an upgrade. The cards are often Nvidia, but not necessarily. Often, the integrated graphics cannot be fully disabled in BIOS, or things go wrong even when the integrated graphics are disabled in BIOS.
This configuration can lead to a variety of problems, with the most severe being kernel panic at boot time, which results in the inability to either try out the liveCD, or install Ubuntu at all.
Since issues related to the combination of integrated graphics+graphics card show up in many forum categories, I collected a list of references where a solution was proposed. The first of those references comes from Alberto Milone (tseliot in Ubuntu forums), the author of EnvyNG, among other qualifications. You will notice that his HowTo validates the solution you describe here, and it seems reasonable to think that it is the best current solution.
The problem has existed in all versions of Ubuntu since at least version 5.10, and all the way to 27 November 2009 daily releases of 10.4. Strangely, it is possible that 8.04 was not affected. I have checked that the live CD of 8.04 indeed boots properly on affected machines, while none of the other versions do. As illustrated by the following links, other distros are affected as well. As a practical matter, this is very likely to stop many users from installing Linux on entry-level namebrand computers, which seems a shame.

here are the links:
[URL="http://www.albertomilone.com/nvidia_...integrated.txt"]

[/URL][http://www.albertomilone.com/nvidia_int ... grated.txt]("http://www.albertomilone.com/nvidia_intel_integrated.txt")
[http://ubuntuforums.org/showthread.php?t=1256691](http://ubuntuforums.org/showthread.php?t=1256691)
[http://ubuntuforums.org/showthread.php?t=1144043](http://ubuntuforums.org/showthread.php?t=1144043)
[http://ubuntuforums.org/showthread.php?t=675497](http://ubuntuforums.org/showthread.php?t=675497)
[http://ubuntuforums.org/showthread.php?t=1308919](http://ubuntuforums.org/showthread.php?t=1308919)
[https://bugs.launchpad.net/ubuntu/+sour ... +bug/55104]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/55104")
[http://www.bikechatforums.com/viewtopic.php?p=2356664](http://www.bikechatforums.com/viewtopic.php?p=2356664)
[http://www.nvnews.net/vbulletin/showthread.php?t=128934](http://www.nvnews.net/vbulletin/showthread.php?t=128934)
[http://ubuntuforums.org/showthread.php?t=196693](http://ubuntuforums.org/showthread.php?t=196693)
[http://ubuntuforums.org/showthread.php?t=635943](http://ubuntuforums.org/showthread.php?t=635943)
[http://ubuntuforums.org/showthread.php?t=192677](http://ubuntuforums.org/showthread.php?t=192677)
[http://ubuntuforums.org/showthread.php?t=496999](http://ubuntuforums.org/showthread.php?t=496999)
[http://ubuntuforums.org/showthread.php?t=1328043](http://ubuntuforums.org/showthread.php?t=1328043)
[http://ubuntuforums.org/showthread.php?t=1078576](http://ubuntuforums.org/showthread.php?t=1078576)
[http://ubuntuforums.org/showthread.php?t=295133](http://ubuntuforums.org/showthread.php?t=295133)
[http://javadocs.wordpress.com/2008/09/2 ... -gfx-card/]("http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/")
[http://ubuntuforums.org/showthread.php?t=207303](http://ubuntuforums.org/showthread.php?t=207303)
[http://en.opensuse.org/NVidia_Suspend_HOWTO](http://en.opensuse.org/NVidia_Suspend_HOWTO)
[http://mepislovers.org/forums/showthread.php?t=6487](http://mepislovers.org/forums/showthread.php?t=6487)
[http://www.opensubscriber.com/message/s ... 46049.html]("http://www.opensubscriber.com/message/slug@slug.org.au/6446049.html")
[http://ubuntuforums.org/showthread.php?t=126492](http://ubuntuforums.org/showthread.php?t=126492)

---

### Post by perez08319 on 2010-03-07
I had the same problem and this solved it. Awesome!!!

---

